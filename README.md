# pgm4
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/b3"
    tools:context=".MainActivity">

    <Button
        android:layout_width="187dp"
        android:layout_height="60dp"
        android:background="@color/white"
        android:id="@+id/sms"
        android:text="SMS"
        android:textSize="25dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.181" />

    <Button
        android:layout_width="187dp"
        android:layout_height="60dp"
        android:id="@+id/call"
        android:background="@color/white"
        android:text="CALL"
        android:textSize="25dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.324" />

    <Button
        android:layout_width="187dp"
        android:layout_height="60dp"
        android:background="#0288D1"
        android:id="@+id/email"
        android:text="EMAIL"
        android:textSize="25dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.47" />

    <Button
        android:layout_width="187dp"
        android:layout_height="60dp"
        android:background="#0288D1"
        android:id="@+id/brows"
        android:text="BROWSER"
        android:textSize="25dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.614" />

    <Button
        android:layout_width="187dp"
        android:layout_height="60dp"
        android:background="#0288D1"
        android:id="@+id/map"
        android:text="MAP"
        android:textSize="25dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.774" />

</androidx.constraintlayout.widget.ConstraintLayout>


MainActivity.java

package com.example.exercise7;

import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {
    Button sms,call,email,brows,map;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);


        sms=findViewById(R.id.sms);
        call=findViewById(R.id.call);
        email=findViewById(R.id.email);
        brows=findViewById(R.id.brows);
        map=findViewById(R.id.map);

        sms.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Uri urisms=Uri.parse("smsto:"+"9544013556");
                Intent i=new Intent(Intent.ACTION_SENDTO,urisms);
                startActivity(i);
            }
        });
        call.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Uri uricall=Uri.parse("tel:"+"9544013556");
                Intent i=new Intent(Intent.ACTION_DIAL,uricall);
                startActivity(i);
            }
        });
        email.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Uri urimail=Uri.parse("mailto:"+"nireekshad114@gmail.com");
                Intent i=new Intent(Intent.ACTION_SENDTO,urimail);
                startActivity(i);
            }
        });
        brows.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Uri uribrows=Uri.parse("https://www.google.com/");
                Intent i=new Intent(Intent.ACTION_VIEW,uribrows);
                startActivity(i);
            }
        });
        map.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Uri urimap=Uri.parse("https://maps.app.goo.gl/GaUWmn993SUB8ieN6");
                Intent i=new Intent(Intent.ACTION_VIEW,urimap);
                startActivity(i);
            }
        });
    }
}



AndroidMaifestFile.xml

<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <uses-feature
        android:name="android.hardware.telephony"
        android:required="false" />
    <uses-permission android:name="android.permission.SEND_SMS">

    </uses-permission>
    <uses-permission android:name="android.permission.CALL_PHONE">

    </uses-permission>
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Exercise7"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
