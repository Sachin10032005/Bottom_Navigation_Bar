# Flutter Bottom Navigation Bar Example

This Flutter project demonstrates the use of a **Bottom Navigation Bar** to switch between different screens (or widgets). The app consists of a simple interface with three navigation options: Home, Contact, and Settings.

## Features
- **Home Page**: Displays a text message "Home Page".
- **Contact Page**: Displays a message "Check Your Contact".
- **Settings Page**: Displays a message "Settings Opened".
- **Bottom Navigation Bar**: Used to switch between these three pages.
- ## Code Overview

The project consists of the following key components:

- `MyApp`: The root widget that sets up the basic structure of the app.
- `MyStatefulWidget`: A stateful widget that manages the current index of the selected tab and updates the displayed widget accordingly.
- **Bottom Navigation Bar**: A navigation bar with three items — Home, Contact, and Settings — that allows users to navigate between the different screens.

### Main Code Snippets

- **`_widgetOptions`**: A list of three widgets that correspond to the Home, Contact, and Settings pages.
- **`_onItemTapped`**: A function that updates the state when a user taps on a BottomNavigationBarItem, changing the index and the displayed content.

### Code

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  static const String _title = "Flutter Code Sample";

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: _title,
      home: MyStatefulWidget(),
    );
  }
}

class MyStatefulWidget extends StatefulWidget {
  MyStatefulWidget({Key? key}) : super(key: key);

  @override
  _MyStatefulWidgetState createState() => _MyStatefulWidgetState();
}

class _MyStatefulWidgetState extends State<MyStatefulWidget> {
  int _selectedIndex = 0;
  static const TextStyle optionStyle =
      TextStyle(fontSize: 30, fontWeight: FontWeight.bold);
  static const List<Widget> _widgetOptions = <Widget>[
    Text(
      'Home Page',
      style: optionStyle,
    ),
    Text(
      'Check Your Contact',
      style: optionStyle,
    ),
    Text(
      'Settings Opened',
      style: optionStyle,
    ),
  ];

  void _onItemTapped(int index) {
    setState(() {
      _selectedIndex = index;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Bottom Navigation Bar'),
        backgroundColor: Colors.red,
      ),
      body: Center(
        child: _widgetOptions.elementAt(_selectedIndex),
      ),
      bottomNavigationBar: BottomNavigationBar(
        items: const <BottomNavigationBarItem>[
          BottomNavigationBarItem(
            icon: Icon(Icons.home),
            label: 'Home',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.phone),
            label: 'Contact ',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.settings),
            label: 'Settings',
          ),
        ],
        currentIndex: _selectedIndex,
        selectedItemColor: Colors.amber[800],
        onTap: _onItemTapped,
      ),
    );
  }
}
