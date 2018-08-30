源代码
```
private void loopTest(){
        int i=0;
        while(i<100){
            Log.d("aaa","a");
            int j=0;
            if(j>50){
                break;
            }
            while (j<i){
                Log.d("aaa","b");

                if(i>50){
                    break;
                }
                int m=0;
                while (m<j){
                    Log.d("aaa","c");
                    if(i>50){
                        break;
                    }
                    Log.d("aaa","d");
                    m++;
                }
                Log.d("aaa","e");
                j++;
            }
            Log.d("aaa","f");
            i++;

        }


    }
```
jimple码
```
private void loopTest()
    {
        loop.asynctask.soot.cbq.myapplication.MainActivity $r0;
        int $i0, $i1, $i2;

        $r0 := @this: loop.asynctask.soot.cbq.myapplication.MainActivity;

        $i0 = 0;

     label1:
        if $i0 >= 100 goto label8;

        staticinvoke <android.util.Log: int d(java.lang.String,java.lang.String)>("aaa", "a");

        $i1 = 0;

        goto label5;

     label2:
        $i2 = 0;

     label3:
        if $i2 >= $i1 goto label4;

        staticinvoke <android.util.Log: int d(java.lang.String,java.lang.String)>("aaa", "c");

        if $i0 <= 50 goto label7;

     label4:
        staticinvoke <android.util.Log: int d(java.lang.String,java.lang.String)>("aaa", "e");

        $i1 = $i1 + 1;

     label5:
        if $i1 >= $i0 goto label6;

        staticinvoke <android.util.Log: int d(java.lang.String,java.lang.String)>("aaa", "b");

        if $i0 <= 50 goto label2;

     label6:
        staticinvoke <android.util.Log: int d(java.lang.String,java.lang.String)>("aaa", "f");

        $i0 = $i0 + 1;

        goto label1;

     label7:
        staticinvoke <android.util.Log: int d(java.lang.String,java.lang.String)>("aaa", "d");

        $i2 = $i2 + 1;

        goto label3;

     label8:
        return;
    }
```
语句解释
```
****  [ JIdentityStmt: $r0 := @this: loop.asynctask.soot.cbq.myapplication.MainActivity, ] 
****  [ JAssignStmt: $i0 = 0, ] 
****  [ JIfStmt: if $i0 >= 100 goto return, ] 
****  [ JInvokeStmt: staticinvoke <android.util.Log: int d(java.lang.String,java.lang.String)>("aaa", "a"), ] 
****  [ JAssignStmt: $i1 = 0, ] 
****  [ JGotoStmt: goto [?= (branch)], ] 
****  [ JAssignStmt: $i2 = 0, ] 
****  [ JIfStmt: if $i2 >= $i1 goto staticinvoke <android.util.Log: int d(java.lang.String,java.lang.String)>("aaa", "e"), ] 
****  [ JInvokeStmt: staticinvoke <android.util.Log: int d(java.lang.String,java.lang.String)>("aaa", "c"), ] 
****  [ JIfStmt: if $i0 <= 50 goto staticinvoke <android.util.Log: int d(java.lang.String,java.lang.String)>("aaa", "d"), ] 
****  [ JInvokeStmt: staticinvoke <android.util.Log: int d(java.lang.String,java.lang.String)>("aaa", "e"), ] 
****  [ JAssignStmt: $i1 = $i1 + 1, ] 
****  [ JIfStmt: if $i1 >= $i0 goto staticinvoke <android.util.Log: int d(java.lang.String,java.lang.String)>("aaa", "f"), ] 
****  [ JInvokeStmt: staticinvoke <android.util.Log: int d(java.lang.String,java.lang.String)>("aaa", "b"), ] 
****  [ JIfStmt: if $i0 <= 50 goto $i2 = 0, ] 
****  [ JInvokeStmt: staticinvoke <android.util.Log: int d(java.lang.String,java.lang.String)>("aaa", "f"), ] 
****  [ JAssignStmt: $i0 = $i0 + 1, ] 
****  [ JGotoStmt: goto [?= (branch)], ] 
****  [ JInvokeStmt: staticinvoke <android.util.Log: int d(java.lang.String,java.lang.String)>("aaa", "d"), ] 
****  [ JAssignStmt: $i2 = $i2 + 1, ] 
****  [ JGotoStmt: goto [?= (branch)], ] 
****  [ JReturnVoidStmt: return, ] 

```
