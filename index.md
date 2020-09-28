# Formulir & Validation

Form merupakan fasilitas untuk menginput data, memiliki banyak bentuk tergantung bentuk data yang akan diinput. namun tidak hanya input data form juga dapat menginformasikan keakuratan data yang diinput seperti batasan data, kesesuaian data dan lain sebagainya.

>## Form Tanpa Validasi

Siapkan Class dengan jenis Stateful Widget 
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(App());
}

class App extends StatelessWidget {
  Widget build(context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(
          title: Text('Form Registrasi'),
        ),
        body: RegisterScreen(),
      ),
    );
  }
}

class RegisterScreen extends StatefulWidget {
  createState() {
    return RegisterScreenState();
  }
}

class RegisterScreenState extends State<RegisterScreen> {
  Widget build(context) {
    return Container(child: Text("Formulir"));
  }
}
```


Tambahkan komponen form pada class RegisterScreenState dengan widget yang diperlukan
dalam contoh ini akan diinput nama, email dan password

```dart
class RegisterScreenState extends State<RegisterScreen> {

  Widget build(context) {
    return Container(
      margin: EdgeInsets.all(20.0),
      child: Form( 
        child: Column( 
          
          children: [
            nameField(),
            emailField(),
            passwordField(),
            registerButton(),
          ],
        )
      ),
    );
  }

  Widget nameField() {
    return TextFormField(
      decoration: InputDecoration(
        labelText: 'Nama Lengkap' 
      ),
    );
  }

  Widget emailField() {
    return TextFormField(
      keyboardType: TextInputType.emailAddress, 
      decoration: InputDecoration(
        labelText: 'Email',
        hintText: 'email@example.com',
      ),
    );
  }

  Widget passwordField() {
    return TextFormField(
      obscureText: true, 
      decoration: InputDecoration(
        labelText: 'Password',
        hintText: 'Enter Password',
      ),
    );
  }

  Widget registerButton() {
   
    return RaisedButton(
      color: Colors.blueAccent,
      onPressed: () {
      
      },
      child: Text('Daftar'), 
    );
  }
}
```

>## Form Dengan Validasi
masih menggunakan program diatas ubah class RegisterScreenState seperti dibawah
```dart
class RegisterScreenState extends State<RegisterScreen> with Validation {
  final formKey = GlobalKey<FormState>();
  String name = '';
  String email = '';
  String password = '';

  Widget build(context) {
    return Container(
      margin: EdgeInsets.all(20.0),
      child: Form(
          key: formKey,
          child: Column(
            children: [
              nameField(),
              emailField(),
              passwordField(),
              registerButton(),
            ],
          )),
    );
  }

  Widget nameField() {
    return TextFormField(
      decoration: InputDecoration(labelText: 'Nama Lengkap'),
      validator: validateName,
      onSaved: (String value) {
        name = value;
      },
    );
  }

  Widget emailField() {
    return TextFormField(
      keyboardType: TextInputType.emailAddress,
      decoration: InputDecoration(
        labelText: 'Email',
        hintText: 'email@example.com',
      ),
      validator: validateEmail,
      onSaved: (String value) {
        email = value;
      },
    );
  }

  Widget passwordField() {
    return TextFormField(
      obscureText: true,
      decoration: InputDecoration(
        labelText: 'Password',
        hintText: 'Enter Password',
      ),
      validator: validatePassword,
      onSaved: (String value) {
        password = value;
      },
    );
  }

  Widget registerButton() {
    return RaisedButton(
      color: Colors.blueAccent,
      onPressed: () {
        if (formKey.currentState.validate()) {
          formKey.currentState.save();
        }
      },
      child: Text('Daftar'),
    );
  }
}
```
tambahkan class validation

``dart
class Validation {
  String validatePassword(String value) {
    if (value.length < 4) {
      return 'Password Minimal 4 Karakter';
    }
    return null;
  }

  String validateEmail(String value) {
    if (!value.contains('@')) {
      return 'Email tidak valid';
    }
    return null;
  }

  String validateName(String value) {
    if (value.isEmpty) {
      return 'Nama Lengkap Harus Diisi';
    }
    return null;
  }
}
```

Selesai





