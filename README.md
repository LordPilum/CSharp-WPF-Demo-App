# CSharp-WPF-Demo-App
Simple WPF App &amp; MongoDB &amp; Design Patterns

# Demo
![alt text](https://github.com/claudiu04/CSharp-WPF-Demo-App/blob/master/DemoAppWPF.PNG)

# Index
1. WPF App
2. MongoDB
3. Architecture
4. Resources

# 1. WFP App
  The Demo App was intended to create a solid implementations of the whole chain from getting the data from Database, display it on a     table grid, as well as proccessing the main query operations from backend to frontend.

  The solution has been splited into three main projects. One WPF project, and two shared projects, intended to be easily decompled,       testable, suitable to be shared across multiple platforms.

NUGETS
  In order to support, C# WPF, MongoDB, or data manimlation functionalities and ease the development process. I have used in this         solution the following nuget libraries:
  - JSON and Newtonsoft.Json
  - MOngoDB.Driver, MongoDBBson, MongoDB.Driver.Core
  - MvvmDialogs
  - Xceed.Wpf.Toolkit, Xceed.Wpf.DataGrid
  - log4net

# 2. MongoDB
  Once you have installed MongoDB, you would need to configure the access, as well as where the data is located.

  To do this, create a file locally, named mongod.cfg. This will include setting path to the data folder for MongoDB server, as well as   to the MongoDB log file, initially without any authentication. Please update these local paths, with your own settings:
  
[Settings]
  {
  systemLog:
    destination: file
    path: "C:\\tools\\mongodb\\db\\log\\mongo.log"
    logAppend: true
  storage:
    dbPath: "C:\\tools\\mongodb\\db\\data"
  }
  
  Run in command prompt next line. This will start the MongoDB server, pointing to the configuration file already created (in case the     server is installed in a custom folder, please update first the command):
[Command Line]
  {
    "C:\Program Files\MongoDB\Server\3.6\bin\mongod.exe" --config C:\Dev\Data.Config\mongod.cfg
  }
  
  Once the server is started (and you could see the details in the log file), run mongo.exe in command prompt. The next step is to add     the administrator user to the database. Run mongodb with the full path (ex: “C:\Program Files\MongoDB\Server\3.6\bin\mongod.exe”).
  
MongoDB .NET Driver
  To connect to MongoDB, add via Nuget the package named MongoDB.Driver. This is the new official driver for .NET, fully supporting the   ASP.NET Core applications. C# comes out with some really great help supporting modern queryies and out-of-box methods implemnting       MongoDB, but to make it easier to work and decouple from the main project implementation, all CRUD, Database-related Logic, and DTOs     have sealed into a separate project called DataAccessDAL. 
  
  
# 3. Architecture
  The App is splited into three main projects. One WPF project, and two shared projects, intended to be easily decompled, testable,   be   suited to be shared across multiple platforms;
  - DataAccessDAL project is reposnisble for CRUD operations, DTOs, as well as communicating and interacting with the database. 
  - DataLogicBAL project is responsible for all the Business Logic operations, managing the overall styles, elements and components via     the CMS layer, as well as bringing and accommodating the DAL project layer for further use acrross platforms.  
  - WPF APP, responsible for rendering, and managing the information details about a Person. 
  
Solution Project
    DAL             -> DataAccess
      CRUD
      DTO
    BAL             -> DataLogic
      BusinessLogic
      CMS  
    WPF App         -> Desktop APP 
      Controls
      Models
      Resources
      Utils
      ViewModels
      Views
    UnitTesting      -> Testing ???
    
# 4. Resources
  A. http://api.mongodb.com/csharp/current/html/R_Project_CSharpDriverDocs.htm
  B. https://github.com/mongodb/mongo-csharp-driver
  C. https://blog.oz-code.com/how-to-mongodb-in-c-part-1/
  D. https://blog.oz-code.com/how-to-mongodb-in-c-part-2/
