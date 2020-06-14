# Convert-Json-To-Object-with-backslash-double-quotes-in-data
The nessesary replacements for an JSON to convert succefully in Object 

* Initial String:  
&nbsp;&nbsp;{  
&nbsp;&nbsp;&nbsp;&nbsp;\"name\":\"John\",  
&nbsp;&nbsp;&nbsp;&nbsp;\"age\":30,  
&nbsp;&nbsp;&nbsp;&nbsp;\"car\":\"null\",  
&nbsp;&nbsp;&nbsp;&nbsp;\"data\":\"testData **\"** Characteres in double quotes **\"** testData\"   !!!!!!!!
&nbsp;&nbsp;}  
* Initial Serialized String:  
&nbsp;&nbsp;{  
&nbsp;&nbsp;&nbsp;&nbsp;\\\"name\\\":\\\"John\\\",  
&nbsp;&nbsp;&nbsp;&nbsp;\\\"age\\\":30,  
&nbsp;&nbsp;&nbsp;&nbsp;\\\"car\\\":\\\"null\\\",  
&nbsp;&nbsp;&nbsp;&nbsp;\\\"data\\\":\\\"testData\\\"Characteres in double quotes\\\"testData\\\"  
&nbsp;&nbsp;}  
* String After Replacements:  
&nbsp;&nbsp;{  
&nbsp;&nbsp;&nbsp;&nbsp;"name":"John",  
&nbsp;&nbsp;&nbsp;&nbsp;"age":30,  
&nbsp;&nbsp;&nbsp;&nbsp;"car":"null",  
&nbsp;&nbsp;&nbsp;&nbsp;"data":"testData\\"Characteres in double quotes\\"testData"  
&nbsp;&nbsp;}

## Steps to clear JSON
```
str = str.Replace("\\\",\\\"", "\",\"");
str = str.Replace("{\\\"", "{\"");
str = str.Replace("\\\"}", "\"}");
str = str.Replace("\\\":\\\"", "\":\"");
str = str.Replace(",\\\"", ",\"");
str = str.Replace("\\\":", "\":");
```

### C#

```
using Newtonsoft.Json;
using System;

namespace Convert_Json_to_Object
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Convert JSON with backslash double quote in Data Field");
            var str = "{\\\"name\\\":\\\"John\\\",\\\"age\\\":30,\\\"car\\\":\\\"null\\\",\\\"data\\\":\\\"testData\\\"Characteres in double quotes\\\"testData\\\"}";
            Console.WriteLine("Initial Object:"+str);
            str = str.Replace("\\\",\\\"", "\",\"");
            str = str.Replace("{\\\"", "{\"");
            str = str.Replace("\\\"}", "\"}");
            str = str.Replace("\\\":\\\"", "\":\"");
            str = str.Replace(",\\\"", ",\"");
            str = str.Replace("\\\":", "\":");
            Console.WriteLine("Object after replacement:"+str);
            object obj = JsonConvert.DeserializeObject<object>(str);
            obj.ToString();
            Console.WriteLine("Serialized Object:"+JsonConvert.SerializeObject(obj));
        }
    }
}
```
New word
