# BeciyeApp
training
// import 'dart:nativewrappers/_internal/vm/lib/ffi_allocation_patch.dart';

import 'package:flutter/cupertino.dart';
// import 'package:flutter/foundation.dart';
import 'package:flutter/material.dart';
import 'package:flutter_svg_provider/flutter_svg_provider.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

 
  @override
  Widget build(BuildContext context) {
     final carrentWidth = MediaQuery.of(context).size.width;
    // double screenHeight = MediaQuery.of(context).size.height;
    return  MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Flutter Demo',
      theme: ThemeData(
        
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.white),
        useMaterial3: true,
      ),
     home: Scaffold(
        body: SafeArea(
          child: Column(
          children: [
            MyHomePage( ),
            search(),
            // alaab(),
            Dalab(),
           Expanded(child: Padding(
            
            padding: EdgeInsets.only(left: 30,right: 30,top: 30),
             child:  GridView.builder(
             itemCount: Plant.plantList.length,
              gridDelegate:  SliverGridDelegateWithFixedCrossAxisCount(
              
              crossAxisCount:2,
              crossAxisSpacing: 12,
              mainAxisSpacing: 12,
              childAspectRatio: 0.7,

              
              ), itemBuilder: (context,index){
                 final plant = Plant.plantList[index];
          return PlantItemCard(plant: plant);
    
              }
           ))
            )  ],
        ),
      ) 
    ));
  
  }

}
class MyHomePage extends StatelessWidget {
  const MyHomePage({super.key});

  @override
  Widget build(BuildContext context) {
    return const Column(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        Padding(
          padding: EdgeInsets.only(left: 10),
          child: Text('Welcome to', style: TextStyle(
            color: Colors.black, fontSize: 25,
            fontWeight: FontWeight.w400,
            
          ),),
        ),
        
        Row(
          children: [
            
            Padding(
              padding: EdgeInsets.only(left:5),
              child: Text('Beeciye Shopping',style: TextStyle(
                color: Colors.orangeAccent,fontSize: 35,
                fontWeight:FontWeight.bold,
                
              ),),
            ),
             
                 
               
            
           
            
          ],
        ),
        
    // SizedBox(            
    // child: Padding(
    //       padding: EdgeInsets.all(20),
    //          child: Image(image: AssetImage('assets/beeciye.png')),
    //            ),
    //           ),
            //       Padding(
            //   padding: EdgeInsets.all(8.0),
            //   child: Image(
            //     width: 32,
            //     height: 32,
            //     image: Svg('assets/12.svg'),
            //   ),
            // )
        
     
     ],
    
    
    );
  }
}
class search extends StatelessWidget {
  const search({super.key});

  @override
  Widget build(BuildContext context) {
    return  Padding(
      
      padding: EdgeInsets.all(12),
      child: Row (
        children: [
          Expanded(child: TextField(
            decoration: InputDecoration(
             hintText: 'Search' ,
            fillColor: Colors.black12,
            filled: true,
            border: OutlineInputBorder(
              borderRadius: BorderRadius.circular(12),
              // borderSide: BorderSide.none
            )
            ),
          )),
           SizedBox(
            
             child: Image(
               width: 32,
               height: 32,
               image: Svg('icons/ss.svg'),
             ),
           )
          
            
          
       ],
      ),
    );
  }
}
// class alaab extends StatelessWidget {
//   const alaab({super.key});

//   @override
//   Widget build(BuildContext context) {
//     return  const SafeArea(
      
//       child: Row(
//         mainAxisAlignment: MainAxisAlignment.spaceAround,
//       children: [
        
//           SizedBox(
//             height: 100,
//             width: 100,
//             child: Padding(
//              padding: EdgeInsets.zero,
//                 child: Image(image: AssetImage('assets/beeciye.png')),
//                   ),
//           ),
                
//              SizedBox(
//               height: 100,
//               width: 100,
//                child: Padding(
//                           padding: EdgeInsets.zero,
//                 child: Image(image: AssetImage('assets/beeciye.png')),
//                   ),
//              ),
//                  SizedBox(
//                   height: 100,
//                   width: 100,
//                    child: Padding(
//                               padding: EdgeInsets.zero,
//                                  child: Image(image: AssetImage('assets/beeciye.png')),
//                                    ),
//                  ),
             
            

//       ],
//       )  );
//   }
// }
class Dalab extends StatefulWidget {
  const Dalab({super.key});

  @override
  State<Dalab> createState() => _dalabState();
}

 class Plant {
  final String name;
  final String price;
  final String image; // Optional property for image

  Plant({
    required this.name,
    required this.price,
    required this.image,
  });

  // Static list of plants
   static List<Plant> plantList = [
    Plant(name: 'Gaari', price: '200',  image: 'assets/car.jpeg'),
    Plant(name: 'Laptop', price: '80', image: 'assets/lab.jpeg'),
    Plant(name: 'Iphone', price: '150', image: 'assets/mo.jpeg'),
    Plant(name: 'Markab', price: '5000', image: 'assets/ship.jpeg'),
  ];
}
class _dalabState extends State<Dalab> {
  int  selectedIndex = 0;
  final List<String> catogories = [
      "Shop",
     "Gym",
       "Sports",
     " CO",

  ];
  @override
  Widget build(BuildContext context) {
    return Padding(
      
      
      padding:  EdgeInsets.only(left: 30,right: 35),
    
      child: SizeChangedLayoutNotifier(
        
        child: Row(
        children:catogories.map((category)  {
          int index = catogories.indexOf(category);
          return GestureDetector(
             onTap:(){
              setState(() {
               selectedIndex = index;

                
              });
             },
          
            
            
            child: Padding(
            padding:   EdgeInsets.only(right: 35),
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Text(
                
                category,
            
              style:TextStyle(
                
                fontSize: 12,
                fontWeight: FontWeight.w500,
                 color:  selectedIndex== index?Colors.green
                  : Colors.blue.withOpacity(0.5),
                 
              ),
              ),
              AnimatedContainer(
                duration: const Duration(milliseconds: 200),

                margin: const EdgeInsets.only(top: 7),
                padding:  EdgeInsets.symmetric(horizontal: selectedIndex == index? 20:0,vertical: 2),
                decoration: BoxDecoration(
                  borderRadius: BorderRadius.circular(11),
                  color:  selectedIndex== index?Colors.green
                  : Colors.transparent,
                
                ),
                
              )
              
            ],
          
          ),
          
        )
        );
      
         }) .toList(),
        
      
          )
          
          )
          
          );
          
          
            
  }
       
    
  }
  class PlantItemCard extends StatelessWidget {
    final Plant plant;
  const PlantItemCard({super.key,required this.plant});

  @override
  Widget build(BuildContext context) {
    return  CupertinoButton(
      padding: EdgeInsets.zero,
      onPressed: (){},
      child: Stack(
        children: [
          Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
           Expanded(child:  Image.asset(plant.image)),
          
          Text(
           plant.name,
           style: const TextStyle(
            fontSize: 14,
            fontWeight: FontWeight.w600,
           ), 
          ),

           
          Row(
            children: [
              Text(
               "\$${plant.price}", style: TextStyle(
                fontWeight: FontWeight.w500,
                fontSize: 12,
               ),
                
              )
            ],
          )
           ],
          )
        ],
      ),
    );
  }
}
