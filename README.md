# HidingStatusBar
public abstract  class HidingStatusBarActivity extends AppCompatActivity {

    @TargetApi(Build.VERSION_CODES.LOLLIPOP)
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        if(Build.VERSION.SDK_INT<16){
            getWindow().setFlags(WindowManager.LayoutParams.FLAG_FULLSCREEN, WindowManager.LayoutParams.FLAG_FULLSCREEN);
        }
        else {
            View decorView=getWindow().getDecorView();
            ActionBar actionBar=getSupportActionBar();
            actionBar.hide();
            Window window=getWindow();
            window.setStatusBarColor(Color.TRANSPARENT);
            window.setFlags(WindowManager.LayoutParams.FLAG_TRANSLUCENT_NAVIGATION, WindowManager.LayoutParams.FLAG_TRANSLUCENT_NAVIGATION);
            window.setFlags(WindowManager.LayoutParams.FLAG_TRANSLUCENT_STATUS,WindowManager.LayoutParams.FLAG_TRANSLUCENT_STATUS);
        }
    }

}

To hide the status bar, your activity should extend this activity. 

The style, i am using given below: 
style name="AppTheme" parent="Theme.AppCompat.Light.DarkActionBar"

