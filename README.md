# Test 
import 'package:flutter/material.dart';

class StudentRegistrationForm extends StatefulWidget {
  @override
  _StudentRegistrationFormState createState() => _StudentRegistrationFormState();
}

class _StudentRegistrationFormState extends State<StudentRegistrationForm> {
  final GlobalKey<FormState> _formKey = GlobalKey<FormState>();
  TextEditingController _nameController = TextEditingController();
  TextEditingController _gradeController = TextEditingController();
  TextEditingController _parentEmailController = TextEditingController();

  @override
  void dispose() {
    _nameController.dispose();
    _gradeController.dispose();
    _parentEmailController.dispose();
    super.dispose();
  }

  void _submitForm() {
    if (_formKey.currentState!.validate()) {
      // Perform student registration logic here
      String name = _nameController.text;
      String grade = _gradeController.text;
      String parentEmail = _parentEmailController.text;

      // Print the student details (replace with your logic)
      print('Name: $name');
      print('Grade: $grade');
      print('Parent Email: $parentEmail');
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Student Registration'),
      ),
      body: Padding(
        padding: EdgeInsets.all(16.0),
        child: Form(
          key: _formKey,
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.stretch,
            children: [
              TextFormField(
                controller: _nameController,
                decoration: InputDecoration(labelText: 'Student Name'),
                validator: (value) {
                  if (value!.isEmpty) {
                    return 'Please enter the student name';
                  }
                  return null;
                },
              ),
              SizedBox(height: 16.0),
              TextFormField(
                controller: _gradeController,
                decoration: InputDecoration(labelText: 'Grade'),
                validator: (value) {
                  if (value!.isEmpty) {
                    return 'Please enter the grade';
                  }
                  return null;
                },
              ),
              SizedBox(height: 16.0),
              TextFormField(
                controller: _parentEmailController,
                decoration: InputDecoration(labelText: 'Parent Email'),
                validator: (value) {
                  if (value!.isEmpty) {
                    return 'Please enter the parent email';
                  }
                  return null;
                },
              ),
              SizedBox(height: 16.0),
              ElevatedButton(
                onPressed: _submitForm,
                child: Text('Register'),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
