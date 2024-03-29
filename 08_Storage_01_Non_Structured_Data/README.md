
# Android Projects
### The purpose of this section is to learn and put in practice the next topics.

__08_Storage_01_Non_Structured_Data__:<br>
> - Understanding the 4 types of non structured data storage; App specific, Media Storage, SharedPreferences.

Taken from android guides

#### [Data storage overview ](https://developer.android.com/training/data-storage)

Android uses a file system that's similar to disk-based file systems on other platforms. The system provides several options for you to save your app data.

- __App-specific storage__: Store files that are meant for your app's use only, either in dedicated directories within an internal storage volume or different dedicated directories within external storage. Use the directories within internal storage to save sensitive information that other apps shouldn't access.
- __Shared storage__: Store files that your app intends to share with other apps, including media, documents, and other files.
- __Preferences__: Store private, primitive data in key-value pairs.
- __Databases__: Store structured data in a private database using the __Room persistence library__.

#### Summary options

  
|                  | Type of content | Access method | Permissions needed | Can other apps access? | Files removed on app uninstall? | 
| :--------------  | :-------------- | :------------ | :----------------- | :--------------------- | :------------------------------ | 
| App-specific files|  Files meant for your app's use only | From internal storage, getFilesDir() or getCacheDir() From external storage, getExternalFilesDir() or getExternalCacheDir() | Never needed for internal storage Not needed for external storage when your app is used on devices that run Android 4.4 (API level 19) or higher | No | Yes |
| Media | Shareable media files (images, audio files, videos) | MediaStore API | READ_EXTERNAL_STORAGE when accessing other apps' files on Android 11 (API level 30) or higher READ_EXTERNAL_STORAGE or WRITE_EXTERNAL_STORAGE when accessing other apps' files on Android 10 (API level 29) Permissions are required for all files on Android 9 (API level 28) or lower | Yes, though the other app needs the READ_EXTERNAL_STORAGE permission | No |
| Documents and other files | Other types of shareable content, including downloaded files | Storage Access Framework | None | Yes, through the system file picker | No |
| App preferences | Key-value pairs | Jetpack Preferences library | None | No | Yes |
| Database | Structured data | Room persistence library | None | No | Yes |


#### How to choose

- __How much space does your data require?__<br>
Internal storage has limited space for app-specific data. Use other types of storage if you need to save a substantial amount of data.
- __How reliable does data access need to be?__<br>
If your app's basic functionality requires certain data, such as when your app is starting up, place the data within internal storage directory or a database. App-specific files that are stored in external storage aren't always accessible because some devices allow users to remove a physical device that corresponds to external storage.
- __What kind of data do you need to store?__<br>
If you have data that's only meaningful for your app, use app-specific storage. For shareable media content, use shared storage so that other apps can access the content. For structured data, use either preferences (for key-value data) or a database (for data that contains more than 2 columns).
- __Should the data be private to your app?__<br>
When storing sensitive data—data that shouldn't be accessible from any other app—use internal storage, preferences, or a database. Internal storage has the added benefit of the data being hidden from users.


__08_Storage_01_Non_Structured_Data__:<br>
> - Understanding the 4 types of non structured data storage; App specific, Media Storage, SharedPreferences.


- Concepts, Classes,...
  - __UI__ related
    - __Fragment__ related 
      - __[FragmentStateAdapter__](https://developer.android.com/reference/androidx/viewpager2/adapter/FragmentStateAdapter)
        - behaviour: 
          - getItemCount
          - createFragment
    - __[ViewPager2](https://developer.android.com/jetpack/androidx/releases/viewpager2)__
  - ViewModel related 
    - [__AndroidViewModel__](https://developer.android.com/reference/androidx/lifecycle/AndroidViewModel)
  - Android Framework, Android OS related 
    - androidx.annotation 
      - [__@RequiresApi(Build.VERSION_CODES.M)__](https://developer.android.com/reference/androidx/annotation/RequiresApi)
    - [androidx.core](https://developer.android.com/jetpack/androidx/releases/core)
      - [getSystemService](https://developer.android.com/reference/android/content/Context#getSystemService(java.lang.Class%3CT%3E))
  - Android Framework storage locations related
    - [android.os.storage](https://developer.android.com/reference/android/os/storage/package-summary)
      - [__StorageManager__](https://developer.android.com/reference/android/os/storage/StorageManager)
        - getUuidForPath
        - getAllocatableBytes
        - allocateBytes
    - context 
      - [getExternalFilesDir](https://developer.android.com/reference/android/content/Context#getExternalFilesDir(java.lang.String))
      - [mainLooper](https://developer.android.com/reference/android/os/Looper#getMainLooper())
    - __ContextCompat__
      - getExternalFilesDirs, ...
    - __Environment__
      - attrs and constants: 
        - __MEDIA_MOUNTED__
        - __MEDIA_MOUNTED_READ_ONLY__
  
  - [Shared Preferences](https://developer.android.com/training/data-storage/shared-preferences)
    - context
      - behaviour: 
        - getSharedPreferences
      - [__SharedPreferences__](https://developer.android.com/training/data-storage/shared-preferences)
        - getInt, ...
      - __MODE_PRIVATE__
  - intent 
    - action: __StorageManager.ACTION_MANAGE_STORAGE__

  - Content Provider Storage related
    - Data Storage 
      - [__Cursor__](https://developer.android.com/reference/android/database/Cursor)
        - [getColumnIndexOrThrow](https://developer.android.com/reference/android/database/Cursor#getColumnIndexOrThrow(java.lang.String))
        - [moveToNext](https://developer.android.com/reference/android/database/Cursor#moveToNext())
        - getLong
        - getString
      - [__ContentResolver__](https://developer.android.com/reference/android/content/ContentResolver)
        - loadThumbnail
      - [__MediaImage__](https://developer.android.com/sdk/api_diff/p-dp2-incr/changes/android.media.Image)
  - Multithreading for data storage 
    - [__Handler__](https://betterprogramming.pub/a-detailed-story-about-handler-thread-looper-message-queue-ac2cd9be0d78)
      - handleMessage
      - obtainMessage
      - sendMessage
    - __Message__
      - what

  - Graphics related 
    - [__Bitmap__](https://developer.android.com/reference/android/graphics/Bitmap)




- Kotlin/Java topics
  - [mutableListOf](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/mutable-list-of.html)
  - __[Pair](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-pair/)__
  - [__LocalDateTime__](https://kotlinlang.org/api/kotlinx-datetime/kotlinx-datetime/kotlinx.datetime/-local-date-time/-local-date-time.html)
    - now
  - [forEach](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/for-each.html)
  - [map](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-map/) 
  - [copy](https://kotlinlang.org/docs/data-classes.html)
  - [__File__](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.io/java.io.-file/)
    - behaviour:
      - exists
      - createNewFile
      - bufferedReader
        - useLines
      - createTempFile
      - listFiles
      - lastModified
  - [__String__](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/) 
    - toRegex
  - [__Runnable__](https://docs.oracle.com/javase/8/docs/api/java/lang/Runnable.html)
  - [__Thread__](https://docs.oracle.com/javase/8/docs/api/java/lang/Thread.html)
    - currentThread
      - name
    - start
