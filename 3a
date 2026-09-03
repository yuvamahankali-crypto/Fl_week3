import 'package:flutter/material.dart';

void main() {
  runApp(const ResponsiveUIDemo());
}

class ResponsiveUIDemo extends StatelessWidget {
  const ResponsiveUIDemo({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Responsive UI Demo',
      debugShowCheckedModeBanner: false,
      theme: ThemeData(
        useMaterial3: true,
        primarySwatch: Colors.teal,
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

    return Scaffold(
      appBar: AppBar(
        title: const Text('Responsive UI', style: TextStyle(color: Colors.white)),
        backgroundColor: Colors.teal,
      ),
      body: SingleChildScrollView(
        padding: const EdgeInsets.all(16),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            // Screen Size Header Banner
            Container(
              width: double.infinity,
              padding: const EdgeInsets.all(16),
              color: Colors.amber[100],
              child: Text(
                screenSize.width < 400
                    ? 'Small Screen'
                    : screenSize.width < 800
                        ? 'Medium Screen'
                        : 'Large Screen',
                style: const TextStyle(fontSize: 20, fontWeight: FontWeight.bold),
                textAlign: TextAlign.center,
              ),
            ),
            const SizedBox(height: 16),

            // Adaptive Layout Builder (Row vs Column)
            LayoutBuilder(
              builder: (context, constraints) {
                if (constraints.maxWidth < 600) {
                  return Column(
                    children: buildResponsiveWidgets(),
                  );
                } else {
                  return Row(
                    mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                    children: buildResponsiveWidgets()
                        .map((w) => Expanded(child: w))
                        .toList(),
                  );
                }
              },
            ),
            const SizedBox(height: 16),

            // Orientation Display Block
            OrientationBuilder(
              builder: (context, orientation) {
                return Center(
                  child: Text(
                    orientation == Orientation.portrait ? 'Portrait Mode' : 'Landscape Mode',
                    style: const TextStyle(fontSize: 16, fontWeight: FontWeight.w500),
                  ),
                );
              },
            ),
            const SizedBox(height: 16),

            // Grid Layout Section
            const Text(
              'Responsive GridView:',
              style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
            ),
            const SizedBox(height: 10),
            GridView.count(
              shrinkWrap: true, // Crucial fix: Allows GridView to live inside SingleChildScrollView
              physics: const NeverScrollableScrollPhysics(), // Crucial fix: Delegates scrolling up to parent
              crossAxisCount: screenSize.width < 600 ? 2 : 4,
              crossAxisSpacing: 10,
              mainAxisSpacing: 10,
              children: List.generate(
                8,
                (index) => Container(
                  color: Colors.blue[100 * ((index % 8) + 1)],
                  child: Center(
                    child: Text(
                      'Item ${index + 1}',
                      style: const TextStyle(fontWeight: FontWeight.bold),
                    ),
                  ),
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }

  List<Widget> buildResponsiveWidgets() {
    return [
      Container(
        margin: const EdgeInsets.all(8),
        padding: const EdgeInsets.all(16),
        color: Colors.red[100],
        width: double.infinity,
        child: const Column(
          children: [
            Icon(Icons.phone_android, size: 40, color: Colors.red),
            SizedBox(height: 8),
            Text('Mobile Friendly', style: TextStyle(fontWeight: FontWeight.w500)),
          ],
        ),
      ),
      Container(
        margin: const EdgeInsets.all(8),
        padding: const EdgeInsets.all(16),
        color: Colors.green[100],
        width: double.infinity,
        child: const Column(
          children: [
            Icon(Icons.tablet, size: 40, color: Colors.green),
            SizedBox(height: 8),
            Text('Tablet Ready', style: TextStyle(fontWeight: FontWeight.w500)),
          ],
        ),
      ),
    ];
  }
}
