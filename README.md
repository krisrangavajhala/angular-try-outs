<!DOCTYPE html>

<head>
    <meta charset="utf-8" />
    <title>AngularJS Try Outs</title>
    <script>document.write('<base href="' + document.location + '" />');</script>
    <script data-require="angular.js@1.2.x" src="https://code.angularjs.org/1.2.25/angular.js" data-semver="1.2.25"></script>
</head>

<body ng-app='app'>
   
    <div ng-controller="myController">
     <div ng-repeat="type in uniqueTypes">
         <hello type="type"></hello>
     </div>    
     </div>  
   
<script text="text/javascript">

 var app = angular.module('app',[]);

app.directive('hello',function(){
    console.log('Hi, entred the app directive');
    
 return {
		restrict: 'EA',
		replace: true,
		transclude: true,
		template:'<div>'+
                         '<p>{{type}}</p>'+
                         '<button type="button" ng-click=toggle($parent.$index)>Single                Toggle</button>'+'<div ng-show="scope.on">'+
                             
     '<ul ng-repeat="component in Object.getOwnPropertyNames[scope.component]">'+
     '<li>{{component}}</li>'
     +'</ul>'+
                         '</div>'+
                         '</div>',
     link:function(scope,element,attr){

        console.log(scope);
       scope.on= false; 
         scope.toggle = function($index){
            scope.on = !scope.on;
            var type = scope.uniqueTypes[$index]; 
            if(scope.on===true)
            {
               
                if(typeof(scope.livingMap[type])== undefined)
                {
                    scope.components={}                    
                    scope.livingMap[type] = scope.components;
                }
                    
                for(var item in scope.items){
                  if(item.type === type )
                  {
                    if(item.name in components)
                    {
                      var stages = components[item.name];
                      stages.push(item.stageName);  
                      
                    }
                    else
                    {
                      var stages=[];
                      stages.push(item.stageName);  
                      components[item.name]=stages;
                    }
                  
                  }
                  
                }
                           
            }
         
         }  
       
       }
       
         
     };
    });
    
function myController($scope)
{
    console.log('From controller'+$scope);
    $scope.livingMap={};
    $scope.test = "bar";
   $scope.uniqueTypes=['Animal','Human'];
    var uniqueStage=['A','B'];
    
       
    $scope.items = [
{name: 'Santhosh',
stageName: 'A',
 type:'Human'},
        
{name: 'Rakesh',
stageName: 'B',
 type:'Human'},
        
 {name: 'Santhosh',
stageName: 'B',
 type:'Human'},
        
 {name: 'Lion',
stageName: 'A',
 type:'Animal'},
        
 {name: 'Tiger',
stageName: 'B',
 type:'Animal'},
        
  {name: 'Lion',
stageName: 'B',
 type:'Animal'}      
               
];
    
}

</script>   
   
</body> 


