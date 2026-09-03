import 'package:flutter/material.dart';

void main() => runApp(const MyResponsiveApp());

class MyResponsiveApp extends StatelessWidget {
  const MyResponsiveApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Responsive UI with MediaQuery',
      debugShowCheckedModeBanner: false,
      theme: ThemeData(
        useMaterial3: true,
        primarySwatch: Colors.deepPurple,
      ),
      home: const ResponsiveHomePage(),
    );
  }
}

class ResponsiveHomePage extends StatelessWidget {
  const ResponsiveHomePage({super.key});

  @override
  Widget build(BuildContext context) {
    final screenSize = MediaQuery.of(context).size;
    final double screenWidth = screenSize.width;

    // Breakpoints definitions
    final bool isMobile = screenWidth < 600;
    final bool isTablet = screenWidth >= 600 && screenWidth < 1024;
    final bool isDesktop = screenWidth >= 1024;

    // Responsive Padding configurations
    final EdgeInsets contentPadding = EdgeInsets.symmetric(
      horizontal: isMobile ? 16 : isTablet ? 32 : 64,
      vertical: 20,
    );

    // Responsive Typography configurations
    final double titleFontSize = isMobile ? 24 : isTablet ? 28 : 32;
    final double contentFontSize = isMobile ? 16 : isTablet ? 18 : 20;

    // Responsive structural layout generator
    Widget buildResponsiveLayout() {
      if (isMobile) {
        return Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: _buildWidgets(titleFontSize, contentFontSize),
        );
      } else {
        return Row(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Expanded(
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: _buildWidgets(titleFontSize, contentFontSize),
              ),
            ),
            if (isDesktop) ...[
              const SizedBox(width: 32), // Layout gap for desktop view
              Expanded(
                child: Container(
                  height: 350,
                  color: Colors.grey[200],
                  child: const Center(
                    child: Text(
                      'Extra Panel for Desktop',
                      style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
                    ),
                  ),
                ),
              ),
            ],
          ],
        );
      }
    }

    return Scaffold(
      appBar: AppBar(
        title: const Text("Responsive Layout", style: TextStyle(color: Colors.white)),
        backgroundColor: Colors.deepPurple,
      ),
      body: SingleChildScrollView(
        child: Padding(
          padding: contentPadding,
          child: buildResponsiveLayout(),
        ),
      ),
    );
  }

  // Master method containing central content widgets
  List<Widget> _buildWidgets(double titleFontSize, double contentFontSize) {
    // Standard static purple spectrum colors for error-free rendering
    final List<Color?> purpleShades = [
      Colors.deepPurple[50],
      Colors.deepPurple[100],
      Colors.deepPurple[200],
      Colors.deepPurple[300],
      Colors.deepPurple[400],
      Colors.deepPurple[500],
    ];

    return [
      Text(
        'Welcome to My App',
        style: TextStyle(fontSize: titleFontSize, fontWeight: FontWeight.bold),
      ),
      const SizedBox(height: 20),
      Text(
        'This layout adapts based on screen width using MediaQuery and breakpoints.',
        style: TextStyle(fontSize: contentFontSize),
      ),
      const SizedBox(height: 20),
      Container(
        height: 150,
        width: double.infinity,
        color: Colors.teal[100],
        child: Center(
          child: Text(
            'Responsive Container',
            style: TextStyle(fontSize: contentFontSize, fontWeight: FontWeight.w500),
          ),
        ),
      ),
      const SizedBox(height: 20),
      Wrap(
        spacing: 10,
        runSpacing: 10,
        children: List.generate(
          6,
          (index) => Container(
            width: 100,
            height: 100,
            color: purpleShades[index % purpleShades.length],
            child: Center(
              child: Text(
                'Box ${index + 1}',
                style: const TextStyle(fontWeight: FontWeight.bold),
              ),
            ),
          ),
        ),
      ),
    ];
  }
}
