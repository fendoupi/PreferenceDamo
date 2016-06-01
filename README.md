## prefernce的使用具体使用 ##

**新建一个xml文件夹，建立一个preference.xml的文件**

该布局的根布局一定是PreferenceScreen

在他的下面可以有PreferenceCategory
 		
		<PreferenceCategory 
        android:key="mymessage"  //key 每一个空间对应一个唯一的key
        android:summary="个人信息设置" // 标题下面的一行小字
        android:title="个人信息设置"> // 标题
		</PreferenceCategory>

在PreferenceCategory下面可以有各种基本的preference空间

比如:CheckBoxPreference,DialogPreference,EditTextPreference,ListPreference,SwitchPreference等等

**activity_main.xml文件**

主布局文件中添加一个FrameLayout控件

新建一个PrefFragment的Java文件继承PreferenceFragment 并实现

	 @Override
    public boolean onPreferenceTreeClick(PreferenceScreen preferenceScreen, Preference preference) {
	}

方法


在onCreate方法中

//加载fragment.xml

	addPreferencesFromResource(R.xml.preference);

初始化xml中的控件

在 onPreferenceTreeClick方法中实现相应的逻辑

MainActivity文件当中
设置FragmentManager 添加prefFragment到事务中
 		
		FragmentManager fm = getFragmentManager();
        FragmentTransaction fragmentTransaction = fm.beginTransaction();
        PrefFragment prefFragment = new PrefFragment();
        fragmentTransaction.add(R.id.prefFragment, prefFragment);
        fragmentTransaction.commit();
