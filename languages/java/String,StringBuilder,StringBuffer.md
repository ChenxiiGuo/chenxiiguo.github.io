#The difference between String, StringBuilder and StringBuffer

##Comparison of the efficiency of String, StringBuilder and StringBuffer

```
  public void run() {
        long start, end;
        start = System.currentTimeMillis();
        StringBuilder res = new StringBuilder("abc");
        StringBuffer res2 = new StringBuffer("abc");
        String res3 = "abc";

        for (int i = 0; i < 100000; i++) {

            res = res.append("def");
        }
        end = System.currentTimeMillis();
        System.out.println(end - start); // 10ms

        start = System.currentTimeMillis();
        for (int i = 0; i < 100000; i++) {
            res2 = res2.append("def");
        }
        end = System.currentTimeMillis();
        System.out.println(end - start); // 5ms

        start = System.currentTimeMillis();
        for (int i = 0; i < 100000; i++) {
            res3 += "def";
        }
        end = System.currentTimeMillis();
        System.out.println(end - start);  //4000ms
  }
```
It is obvious that if a string need to always be modified, stringbuffer and stringbuilder is much better. This is due
to the fact that "String" is constent. If you want to do str += "abc", the JVM need to generate a new string. This is a waster
of time. However, if you use Stringbuffer and Stringbuilder, the JVM doesn't need to generate a new object.

## The difference between Stringbuffer and Stringbuilder
Stringbuffer is thread-safe， but Stringbuilder is not.
