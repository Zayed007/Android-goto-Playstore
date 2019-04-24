# Android-goto-Playstore

```
final String appPackageName = getPackageName(); // getPackageName() from Context or Activity object
try {
    startActivity(new Intent(Intent.ACTION_VIEW, Uri.parse("market://details?id=" + appPackageName)));
} catch (android.content.ActivityNotFoundException anfe) {
    startActivity(new Intent(Intent.ACTION_VIEW, Uri.parse("https://play.google.com/store/apps/details?id=" + appPackageName)));
}
```


# Share App

```
private void shareApp(){
        try {
            Intent shareIntent = new Intent(Intent.ACTION_SEND);
            shareIntent.setType("text/plain");
            shareIntent.putExtra(Intent.EXTRA_SUBJECT, getApplicationName(this));
            shareIntent.putExtra(Intent.EXTRA_TEXT,  "https://play.google.com/store/apps/details?id=" + BuildConfig.APPLICATION_ID );
            startActivity(Intent.createChooser(shareIntent, "Share"));
        } catch(Exception e) {
        }
    }

    public static String getApplicationName(Context context) {
        ApplicationInfo applicationInfo = context.getApplicationInfo();
        int stringId = applicationInfo.labelRes;
        return stringId == 0 ? applicationInfo.nonLocalizedLabel.toString() : context.getString(stringId);
    }
```

# My All app at Play store

```
    private void getMyAllApp() {
        Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(pref.myAllAppLink().get()));
        startActivity(browserIntent);
    }
```
