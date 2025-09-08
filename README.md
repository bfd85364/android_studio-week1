# android_studio-week1


<?xml version="1.0" encoding="utf-8"?>
<LinearLayout android:orientation="vertical"
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/Edit1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_margin="15dp"
        android:textSize="10sp"
        android:hint="x1" />

    <EditText
        android:id="@+id/Edit2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="15dp"
        android:textSize="10sp"
        android:hint="x2" />

    <Button
        android:id="@+id/BtnAdd"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="15dp"
        android:textSize="10sp"
        android:text="더하기"/>

    <Button
        android:id="@+id/Btnminus"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="15dp"
        android:textSize="10sp"
        android:text="빼기"/>

    <Button
        android:id="@+id/Btnmulti"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="15dp"
        android:textSize="10sp"
        android:text="곱하기"/>

    <Button
        android:id="@+id/Btndivide"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="15dp"
        android:text="나누기"
        android:textSize="10sp" />

    <TextView
        android:id="@+id/TextResult"
        android:layout_width="378dp"
        android:layout_height="wrap_content"
        android:layout_margin="10dp"
        android:text="계산 결과: "
        android:textColor="#FF0000"
        android:textSize="15sp" />

</LinearLayout>
-------------------------------java 코드------------------------------------------------------------------------------------------------------------------------------------------------------------

package com.example.a202305127_2025_09_08;

import android.os.Bundle;
import android.view.MotionEvent;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {
    EditText Edit1, Edit2;
    Button BtnAdd, Btnminus,Btnmulti,Btndivide;

    TextView TextResult;
    String num1, num2;
    Integer result;




    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);
        setTitle("초간단 계산기");

        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });

        Edit1 = (EditText) findViewById(R.id.Edit1);
        Edit2 = (EditText) findViewById(R.id.Edit2);
        BtnAdd =(Button) findViewById(R.id.BtnAdd);
        Btnminus=(Button) findViewById(R.id.Btnminus);
        Btnmulti=(Button) findViewById(R.id.Btnmulti);
        Btndivide=(Button) findViewById(R.id.Btndivide);
        TextResult = (TextView) findViewById(R.id.TextResult);

        BtnAdd.setOnTouchListener(new View.OnTouchListener(){
            public boolean onTouch(View argO, MotionEvent arg1) {
                num1 = Edit1.getText().toString();
                num2 = Edit2.getText().toString();
                result = Integer.parseInt(num1) + Integer.parseInt(num2);
                TextResult.setText("계산 결과: " + result.toString());
                return false;
            }
        });

        Btnminus.setOnTouchListener(new View.OnTouchListener(){
            public boolean onTouch(View view, MotionEvent motionEvent) {
                num1 = Edit1.getText().toString();
                num2 = Edit2.getText().toString();
                result = Integer.parseInt(num1) - Integer.parseInt(num2);
                TextResult.setText("계산 결과: " + result.toString());
                return false;
            }
        });

        Btnmulti.setOnTouchListener(new View.OnTouchListener() {
            public boolean onTouch(View view, MotionEvent motionEvent) {
                num1 = Edit1.getText().toString();
                num2 = Edit2.getText().toString();
                result = Integer.parseInt(num1) * Integer.parseInt(num2);
                TextResult.setText("계산 결과: " + result.toString());
                return false;
            }
        });

        Btndivide.setOnTouchListener(new View.OnTouchListener() {
            public boolean onTouch(View view, MotionEvent motionEvent) {
                num1 = Edit1.getText().toString();
                num2 = Edit2.getText().toString();
                result = Integer.parseInt(num1)/Integer.parseInt(num2);
                TextResult.setText("계산 결과: " + result.toString());
                return false;
            }
        });


    }
}





