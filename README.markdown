**写在前头:本插件只适用 android studio和 Intellij IDEA 工具,exlipse 的少年无视我吧!!!**
这是一个根据JSONObject格式的字符串,自动生成实体类参数.
  github源码https://github.com/zzz40500/GsonFormat
  GsonFormat下载:http://download.csdn.net/detail/u010637692/8349047
  Usage:
插件安装方法1:
~~~
     1.下载GsonFormat.jar ;
     2.Android studio  File->Settings..->Plugins -->
 install plugin from disk..导入下载的GsonFormat.jar 
     3重启android studio 在一个实体类下使用快捷键generate 的快捷键.
~~~
插件安装方法2:
~~~
1.Android studio  File->Settings..->Plugins-->Browse repositores..搜索gson
2.重启android studio 在一个实体类下使用快捷键generate 的快捷键.
~~~

快捷键:图中选中的部分

![72350A47-A21A-4505-817E-2CA8092F7B7D.png](http://upload-images.jianshu.io/upload_images/166866-45621bdaadaa177c.png)
我这边的快捷键是 command+n;
使用方式:
简单的实体类:
![简单的.gif](http://upload-images.jianshu.io/upload_images/166866-07f3084bb6758efa.gif)
图中简单的 json 格式
~~~
{
    "name": "王五",
    "gender": "man",
    "age": 15,
    "height": "140cm",
}
~~~
图中的实体类
~~~
**
 * Created by 轻微 on 15/1/9.
 */
public class Bean  extends JSONModel {


    /**
     * height : 140cm
     * age : 15
     * name : 王五
     * gender : man
     */
    private String height;
    private int age;
    private String name;
    private String gender;

    public void setHeight(String height) {
        this.height = height;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setGender(String gender) {
        this.gender = gender;
    }

    public String getHeight() {
        return height;
    }

    public int getAge() {
        return age;
    }

    public String getName() {
        return name;
    }

    public String getGender() {
        return gender;
    }
}
~~~
复杂的实体类:
实体类不仅包含另外一个**实体**,还包含另外实体的**数组**.
![复杂.gif](http://upload-images.jianshu.io/upload_images/166866-38c1f99c6d097367.gif)
图中复杂的json 格式
~~~
{
    "name": "王五",
    "gender": "man",
    "age": 15,
    "height": "140cm",
    "addr": {
        "province": "fujian",
        "city": "quanzhou",
        "code": "300000"
    },
    "hobby": [
        {
            "name": "billiards",
            "code": "1"
        },
        {
            "name": "computerGame",
            "code": "2"
        }
    ]
}
~~~
图中的实体类
~~~
/**
 * Created by 轻微 on 15/1/9.
 */
public class Bean  extends JSONModel {


    /**
     * height : 140cm
     * age : 15
     * name : 王五
     * hobby : [{"name":"billiards","code":"1"},{"name":"computerGame","code":"2"}]
     * gender : man
     * addr : {"province":"fujian","code":"300000","city":"quanzhou"}
     */
    private String height;
    private int age;
    private String name;
    private List<HobbyEntity> hobby;
    private String gender;
    private AddrEntity addr;

    public void setHeight(String height) {
        this.height = height;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setHobby(List<HobbyEntity> hobby) {
        this.hobby = hobby;
    }

    public void setGender(String gender) {
        this.gender = gender;
    }

    public void setAddr(AddrEntity addr) {
        this.addr = addr;
    }

    public String getHeight() {
        return height;
    }

    public int getAge() {
        return age;
    }

    public String getName() {
        return name;
    }

    public List<HobbyEntity> getHobby() {
        return hobby;
    }

    public String getGender() {
        return gender;
    }

    public AddrEntity getAddr() {
        return addr;
    }

    public class HobbyEntity {
        /**
         * name : billiards
         * code : 1
         */
        private String name;
        private String code;

        public void setName(String name) {
            this.name = name;
        }

        public void setCode(String code) {
            this.code = code;
        }

        public String getName() {
            return name;
        }

        public String getCode() {
            return code;
        }
    }

    public class AddrEntity {
        /**
         * province : fujian
         * code : 300000
         * city : quanzhou
         */
        private String province;
        private String code;
        private String city;

        public void setProvince(String province) {
            this.province = province;
        }

        public void setCode(String code) {
            this.code = code;
        }

        public void setCity(String city) {
            this.city = city;
        }

        public String getProvince() {
            return province;
        }

        public String getCode() {
            return code;
        }

        public String getCity() {
            return city;
        }
    }
}

~~~






