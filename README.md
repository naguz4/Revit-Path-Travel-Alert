# Revit-Path-Travel-Alert
Dynamo script to check exit travel paths
{
  "Uuid": "bf136481-5241-454c-9cfe-b6ea6af56cb8",
  "IsCustomNode": false,
  "Description": null,
  "Name": "Path of Travel Alert",
  "ElementResolver": {
    "ResolutionMap": {}
  },
  "Inputs": [],
  "Outputs": [
    {
      "Id": "132c8c0e48414131aa7c8610ea89c7ef",
      "Name": "PathOfTravel.ByFloorPlanPoints",
      "Type": "unknown",
      "InitialValue": "",
      "Description": "Construct a list of Path of Travel elements in a floor plan view between the specified start points and end points\n\nPathOfTravel.ByFloorPlanPoints (floorPlan: FloorPlanView, startPtList: Point[], endPtList: Point[], manyToMany: bool): PathOfTravel[]..[]"
    }
  ],
  "Nodes": [
    {
      "ConcreteType": "Dynamo.Graph.Nodes.ZeroTouch.DSFunction, DynamoCore",
      "NodeType": "FunctionNode",
      "FunctionSignature": "Revit.Elements.PathOfTravel.ByFloorPlanPoints@Revit.Elements.Views.FloorPlanView,Autodesk.DesignScript.Geometry.Point[],Autodesk.DesignScript.Geometry.Point[],bool",
      "Id": "132c8c0e48414131aa7c8610ea89c7ef",
      "Inputs": [
        {
          "Id": "c604e18da96b4f6c8935a4b869d515a6",
          "Name": "floorPlan",
          "Description": "Floor plan view to place paths of travel on\n\nFloorPlanView",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "be6b5a4f31944b02931c6b0aef12fdb7",
          "Name": "startPtList",
          "Description": "List of start points\n\nPoint[]",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "f9d34452abf04bbab084f07c6f7e3e82",
          "Name": "endPtList",
          "Description": "List of end points\n\nPoint[]",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "bd70505e5091473eb1b716c043b5d86a",
          "Name": "manyToMany",
          "Description": "If true, paths are created from every point in the start point list to all points in the end point list. If false, a path is created from every point in the start point list to a corresponding point in the end point list with the same index. The two lists must have the same size when not creating many-to-many paths.\n\nbool",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Outputs": [
        {
          "Id": "060f926f03fe496da0d26dd4fc81c533",
          "Name": "PathOfTravel[]..[]",
          "Description": "List of Path of Travel elements; can contain null elements if there is no path between some points.",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "CrossProduct",
      "Description": "Construct a list of Path of Travel elements in a floor plan view between the specified start points and end points\n\nPathOfTravel.ByFloorPlanPoints (floorPlan: FloorPlanView, startPtList: Point[], endPtList: Point[], manyToMany: bool): PathOfTravel[]..[]"
    },
    {
      "ConcreteType": "CoreNodeModels.Input.BoolSelector, CoreNodeModels",
      "NodeType": "BooleanInputNode",
      "InputValue": true,
      "Id": "436919e9a2ca40fc9ed3bb97a4df5201",
      "Inputs": [],
      "Outputs": [
        {
          "Id": "48a6335c8f9f441f8b6d0be0bc5646fa",
          "Name": "",
          "Description": "Boolean",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Disabled",
      "Description": "Selection between a true and false."
    },
    {
      "ConcreteType": "Dynamo.Graph.Nodes.ZeroTouch.DSFunction, DynamoCore",
      "NodeType": "FunctionNode",
      "FunctionSignature": "Revit.Elements.Room.Location",
      "Id": "a886a0d815394701863b8c69ff608ea6",
      "Inputs": [
        {
          "Id": "189bcb32aa7742ee9460e3e398062dba",
          "Name": "room",
          "Description": "Revit.Elements.Room",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Outputs": [
        {
          "Id": "02c844015268477d965c0708c58fb086",
          "Name": "Point",
          "Description": "Point",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Auto",
      "Description": "Get Room Location\n\nRoom.Location: Point"
    },
    {
      "ConcreteType": "DSRevitNodesUI.ElementsOfCategory, DSRevitNodesUI",
      "NodeType": "ExtensionNode",
      "Id": "446d42b1aa0b4328af61c6378d4718f6",
      "Inputs": [
        {
          "Id": "c68cd829dc2b4edaaf065db024f7ce7d",
          "Name": "Category",
          "Description": "The Category",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Outputs": [
        {
          "Id": "eef0aca7e50a44cd9642eddb4883834d",
          "Name": "Elements",
          "Description": "An element type.",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Disabled",
      "Description": "Get all elements of the specified category from the model."
    },
    {
      "ConcreteType": "DSRevitNodesUI.Categories, DSRevitNodesUI",
      "SelectedIndex": 428,
      "SelectedString": "OST_Rooms",
      "NodeType": "ExtensionNode",
      "Id": "98384bab1e9e4022b26f2205ea17a702",
      "Inputs": [],
      "Outputs": [
        {
          "Id": "c130e89bf8c34e3c8c4ecb24dfc14925",
          "Name": "Category",
          "Description": "The selected Category.",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Disabled",
      "Description": "All built-in categories."
    },
    {
      "ConcreteType": "Dynamo.Graph.Nodes.ZeroTouch.DSFunction, DynamoCore",
      "NodeType": "FunctionNode",
      "FunctionSignature": "DSCore.List.Clean@var[]..[],bool",
      "Id": "72dac09e434d4b9ca497aaac1b8d6cf9",
      "Inputs": [
        {
          "Id": "81285b23c3de43e4a47139ed27870197",
          "Name": "list",
          "Description": "var[]..[]",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "287ade5fe56c4cc4995e81efd4391a89",
          "Name": "preserveIndices",
          "Description": "Provide an option to preserve the indices of the data such that non-trailing nulls may not be filtered out\n\nbool\nDefault value : true",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Outputs": [
        {
          "Id": "7fd1a6a827cf4515b322c9162c9e570d",
          "Name": "var[]..[]",
          "Description": "A list cleaned of nulls and empty lists",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Auto",
      "Description": "Cleans data of nulls and empty lists from a given list of arbitrary dimension\n\nList.Clean (list: var[]..[], preserveIndices: bool = true): var[]..[]"
    },
    {
      "ConcreteType": "CoreNodeModels.Input.BoolSelector, CoreNodeModels",
      "NodeType": "BooleanInputNode",
      "InputValue": false,
      "Id": "8c5d02115d324e97a46b528e1cea6bfa",
      "Inputs": [],
      "Outputs": [
        {
          "Id": "c8a02d93936443c49fb910479799648d",
          "Name": "",
          "Description": "Boolean",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Disabled",
      "Description": "Selection between a true and false."
    },
    {
      "ConcreteType": "Dynamo.Nodes.DSModelElementSelection, DSRevitNodesUI",
      "NodeType": "ExtensionNode",
      "InstanceId": [
        "7a5be65e-c956-44ba-ae5c-4b9df3eafdaf-005129e3"
      ],
      "Id": "b57c2682f6b3412281bf06104f1a8767",
      "Inputs": [],
      "Outputs": [
        {
          "Id": "9a01b59923584397bde514587188f470",
          "Name": "Element",
          "Description": "The selected elements.",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Disabled"
    },
    {
      "ConcreteType": "Dynamo.Graph.Nodes.ZeroTouch.DSFunction, DynamoCore",
      "NodeType": "FunctionNode",
      "FunctionSignature": "Revit.Elements.Element.GetLocation",
      "Id": "7af791e506d1467488b1a073e268862b",
      "Inputs": [
        {
          "Id": "51a4fac869c34fa28d932569f8220aa6",
          "Name": "element",
          "Description": "Revit.Elements.Element",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Outputs": [
        {
          "Id": "942779ba654f450b93ba6bcb1ee92e71",
          "Name": "Geometry",
          "Description": "Location Geometry",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Auto",
      "Description": "Get an existing element's location\n\nElement.GetLocation ( ): Geometry"
    },
    {
      "ConcreteType": "DSRevitNodesUI.Views, DSRevitNodesUI",
      "SelectedIndex": 1,
      "SelectedString": "0-Master Plan",
      "NodeType": "ExtensionNode",
      "Id": "beeb9cc8de98440aa883bd081bfbae18",
      "Inputs": [],
      "Outputs": [
        {
          "Id": "f0930982a3854191aae167611f435564",
          "Name": "Views",
          "Description": "The selected Views",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Disabled",
      "Description": "All views available in the current document."
    },
    {
      "ConcreteType": "CoreNodeModels.CreateList, CoreNodeModels",
      "VariableInputPorts": true,
      "NodeType": "ExtensionNode",
      "Id": "a7c8df3fa8d3434796c3a1a58a48ea3a",
      "Inputs": [
        {
          "Id": "cb190eac18ab454aa0e6132d0d6e9c18",
          "Name": "item0",
          "Description": "Item Index #0",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Outputs": [
        {
          "Id": "62a86696fb8d467e9f82a72573f70022",
          "Name": "list",
          "Description": "A list",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Disabled",
      "Description": "Makes a new list out of the given inputs"
    },
    {
      "ConcreteType": "Dynamo.Graph.Nodes.ZeroTouch.DSFunction, DynamoCore",
      "NodeType": "FunctionNode",
      "FunctionSignature": "Revit.Elements.Room.Name",
      "Id": "d075f88152e64da4a9bc4a1c57e89d48",
      "Inputs": [
        {
          "Id": "53730bd2d414492fac8dac928fbda5c6",
          "Name": "room",
          "Description": "Revit.Elements.Room",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Outputs": [
        {
          "Id": "172b39c077814216b6deec0f656d7e63",
          "Name": "string",
          "Description": "string",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Auto",
      "Description": "Get room name\n\nRoom.Name: string"
    },
    {
      "ConcreteType": "Dynamo.Graph.Nodes.ZeroTouch.DSFunction, DynamoCore",
      "NodeType": "FunctionNode",
      "FunctionSignature": "Revit.Elements.Element.GetParameterValueByName@string",
      "Id": "d554667e496848248680d415ccd4ace7",
      "Inputs": [
        {
          "Id": "c3134316008e445f8de449e30778de07",
          "Name": "element",
          "Description": "Revit.Elements.Element",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "5e783995dc334b5094d04375966a9a69",
          "Name": "parameterName",
          "Description": "The name of the parameter whose value you want to obtain.\n\nstring",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Outputs": [
        {
          "Id": "2a22c768698b4fb4a73493666eb9cd34",
          "Name": "var[]..[]",
          "Description": "var[]..[]",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Auto",
      "Description": "Get the value of one of the element's parameters.\n\nElement.GetParameterValueByName (parameterName: string): var[]..[]"
    },
    {
      "ConcreteType": "CoreNodeModels.Input.StringInput, CoreNodeModels",
      "NodeType": "StringInputNode",
      "InputValue": "Length",
      "Id": "38e607ea3af044f4a0ec69bc707742da",
      "Inputs": [],
      "Outputs": [
        {
          "Id": "f30c7952eb0d417fb7e83491d255ff0f",
          "Name": "",
          "Description": "String",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Disabled",
      "Description": "Creates a string."
    },
    {
      "ConcreteType": "Dynamo.Graph.Nodes.ZeroTouch.DSFunction, DynamoCore",
      "NodeType": "FunctionNode",
      "FunctionSignature": "DSCore.List.Clean@var[]..[],bool",
      "Id": "3136b1340c3a46509e61bd27ced517b1",
      "Inputs": [
        {
          "Id": "7b56da3191ff4a818e838a84ca2af523",
          "Name": "list",
          "Description": "var[]..[]",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "ad65a0c5400a421db46f89cd726fb132",
          "Name": "preserveIndices",
          "Description": "Provide an option to preserve the indices of the data such that non-trailing nulls may not be filtered out\n\nbool\nDefault value : true",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Outputs": [
        {
          "Id": "1b1df20198c2462b8cb594c4ef414f18",
          "Name": "var[]..[]",
          "Description": "A list cleaned of nulls and empty lists",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Auto",
      "Description": "Cleans data of nulls and empty lists from a given list of arbitrary dimension\n\nList.Clean (list: var[]..[], preserveIndices: bool = true): var[]..[]"
    },
    {
      "ConcreteType": "CoreNodeModels.Input.BoolSelector, CoreNodeModels",
      "NodeType": "BooleanInputNode",
      "InputValue": false,
      "Id": "ce176f7fb4d74cd1a96443ac18aa7d33",
      "Inputs": [],
      "Outputs": [
        {
          "Id": "f33fbfb05d2444f6a555821a34c80a81",
          "Name": "",
          "Description": "Boolean",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Disabled",
      "Description": "Selection between a true and false."
    },
    {
      "ConcreteType": "Dynamo.Graph.Nodes.ZeroTouch.DSFunction, DynamoCore",
      "NodeType": "FunctionNode",
      "FunctionSignature": "Revit.Elements.Element.OverrideInView@Revit.Filter.OverrideGraphicSettings,bool",
      "Id": "4a5f0fdca88e40ac95cd866b1f945dc2",
      "Inputs": [
        {
          "Id": "30a24438ea894c9ba72d84e8fa365954",
          "Name": "element",
          "Description": "Revit.Elements.Element",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "50749568ba574df49d036073d3111ee7",
          "Name": "overrides",
          "Description": "Override Graphics Settings.\n\nOverrideGraphicSettings",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "bbcdb729fad442938140be800d0a19e8",
          "Name": "hide",
          "Description": "If True given Element will be hidden.\n\nbool\nDefault value : false",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Outputs": [
        {
          "Id": "89fca5a16766411e9ee3a8f90ac35da3",
          "Name": "Element",
          "Description": "Element",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Longest",
      "Description": "Override Elements Graphics Settings in Active View.\n\nElement.OverrideInView (overrides: OverrideGraphicSettings, hide: bool = false): Element"
    },
    {
      "ConcreteType": "Dynamo.Graph.Nodes.ZeroTouch.DSFunction, DynamoCore",
      "NodeType": "FunctionNode",
      "FunctionSignature": ">@var[]..[],var[]..[]",
      "Id": "6490c4bbffc944aa98677323d13b19a9",
      "Inputs": [
        {
          "Id": "d337346db5134358836469fb348914b0",
          "Name": "x",
          "Description": "x value.\n\nvar[]..[]",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "0ead0e4e461e43528cbd8baf5266153a",
          "Name": "y",
          "Description": "y value.\n\nvar[]..[]",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Outputs": [
        {
          "Id": "7ea99569925d4a30a00c9f287c484e29",
          "Name": "var[]..[]",
          "Description": "var[]..[]",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Auto",
      "Description": "x greater y?\n\n> (x: var[]..[], y: var[]..[]): var[]..[]"
    },
    {
      "ConcreteType": "Dynamo.Graph.Nodes.CodeBlockNodeModel, DynamoCore",
      "NodeType": "CodeBlockNode",
      "Code": "20000;",
      "Id": "a859ab6891b64a4192bb3dcc0dd627a9",
      "Inputs": [],
      "Outputs": [
        {
          "Id": "6d8208ed3d434c4a99b565309d45eb98",
          "Name": "",
          "Description": "Value of expression at line 1",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Disabled",
      "Description": "Allows for DesignScript code to be authored directly"
    },
    {
      "ConcreteType": "Dynamo.Graph.Nodes.ZeroTouch.DSFunction, DynamoCore",
      "NodeType": "FunctionNode",
      "FunctionSignature": "DSCore.List.FilterByBoolMask@var[]..[],var[]..[]",
      "Id": "56996316836e4c62a83ceaf0a3091dd9",
      "Inputs": [
        {
          "Id": "b60f1fd7f23a4624a2316fa0ef840d7b",
          "Name": "list",
          "Description": "List to filter.\n\nvar[]..[]",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "1e040db4bf5b4887bb538c1f26477d14",
          "Name": "mask",
          "Description": "List of booleans representing a mask.\n\nvar[]..[]",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Outputs": [
        {
          "Id": "fdf82c8d73554a84add39182a4525e3e",
          "Name": "in",
          "Description": "Items whose mask index is true.",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "904473149b404113ae24048cef25d4ed",
          "Name": "out",
          "Description": "Items whose mask index is false.",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Auto",
      "Description": "Filters a sequence by looking up corresponding indices in a separate list of booleans.\n\nList.FilterByBoolMask (list: var[]..[], mask: var[]..[]): var[]..[]"
    },
    {
      "ConcreteType": "Dynamo.Graph.Nodes.ZeroTouch.DSFunction, DynamoCore",
      "NodeType": "FunctionNode",
      "FunctionSignature": "DSCore.List.Transpose@var[]..[]",
      "Id": "ed2ac9548d834b2f809801fc78bd1ecf",
      "Inputs": [
        {
          "Id": "a59f8715d6b34a51beabfb63233dde96",
          "Name": "lists",
          "Description": "A list of lists to be transposed.\n\nvar[]..[]",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Outputs": [
        {
          "Id": "6c961d5129b8468d9ed85e55fb8db7b0",
          "Name": "lists",
          "Description": "A list of transposed lists.",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Auto",
      "Description": "Swaps rows and columns in a list of lists. If there are some rows that are shorter than others, null values are inserted as place holders in the resultant array such that it is always rectangular.\n\nList.Transpose (lists: var[]..[]): var[]..[]"
    },
    {
      "ConcreteType": "Dynamo.Graph.Nodes.ZeroTouch.DSFunction, DynamoCore",
      "NodeType": "FunctionNode",
      "FunctionSignature": "Revit.Filter.OverrideGraphicSettings.ByProperties@DSCore.Color,DSCore.Color,DSCore.Color,DSCore.Color,Revit.Elements.FillPatternElement,Revit.Elements.FillPatternElement,Revit.Elements.LinePatternElement,Revit.Elements.LinePatternElement,int,int,int,string,bool",
      "Id": "5831251f0b3445b1ba0c77462a1c6b5c",
      "Inputs": [
        {
          "Id": "2ea0024f3511419a9e105a764e084053",
          "Name": "cutFillColor",
          "Description": "Fill color\n\nColor\nDefault value : null",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "5a6cdd588579411f81a4940fcda36bbd",
          "Name": "projectionFillColor",
          "Description": "Projection color\n\nColor\nDefault value : null",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "f6174fbaef774f7ea40c982329b4d08d",
          "Name": "cutLineColor",
          "Description": "Cut line color\n\nColor\nDefault value : null",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "ecb7d1ef87774dc0a117f4df657fbdf5",
          "Name": "projectionLineColor",
          "Description": "Projection line color\n\nColor\nDefault value : null",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "78a81edee58f4e24b07a7a5c047d1a3a",
          "Name": "cutFillPattern",
          "Description": "Cut fill pattern\n\nFillPatternElement\nDefault value : null",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "b716fcd6deb540d088ca1d7a8d401a37",
          "Name": "projectionFillPattern",
          "Description": "Projection fill pattern\n\nFillPatternElement\nDefault value : null",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "d4357d7fff234b529b68aaddbb129b05",
          "Name": "cutLinePattern",
          "Description": "Cut line pattern\n\nLinePatternElement\nDefault value : null",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "d87c52a281b14153804b1c419490459d",
          "Name": "projectionLinePattern",
          "Description": "Projection line pattern\n\nLinePatternElement\nDefault value : null",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "1ff9dce04b6b419cae2fddc55b1fe36c",
          "Name": "cutLineWeight",
          "Description": "Cut line weight\n\nint\nDefault value : -1",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "99f13ebe27a84bc2a8cf557c41c457d0",
          "Name": "projectionLineWeight",
          "Description": "Projection line weight\n\nint\nDefault value : -1",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "9ac247f0f59b4190a43f054587d9fed8",
          "Name": "transparency",
          "Description": "Transparency as integer between 1-100.\n\nint\nDefault value : -1",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "31906f780fae4c218c7dac9567a434c0",
          "Name": "detailLevel",
          "Description": "Detail Level setting, ex: Coarse, Fine etc.\n\nstring\nDefault value : \"Undefined\"",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "9ed64858075b475a9f0c4fb650146472",
          "Name": "halftone",
          "Description": "Halftone. True = halftone.\n\nbool\nDefault value : false",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Outputs": [
        {
          "Id": "7f43ef4fe19b454c80a55a051b8f61a8",
          "Name": "overrides",
          "Description": "Override Graphic Settings",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Auto",
      "Description": "Create a OverrideGraphicSettings Element.\n\nOverrideGraphicSettings.ByProperties (cutFillColor: Color = null, projectionFillColor: Color = null, cutLineColor: Color = null, projectionLineColor: Color = null, cutFillPattern: FillPatternElement = null, projectionFillPattern: FillPatternElement = null, cutLinePattern: LinePatternElement = null, projectionLinePattern: LinePatternElement = null, cutLineWeight: int = -1, projectionLineWeight: int = -1, transparency: int = -1, detailLevel: string = \"Undefined\", halftone: bool = false): OverrideGraphicSettings"
    },
    {
      "ConcreteType": "Dynamo.Graph.Nodes.ZeroTouch.DSFunction, DynamoCore",
      "NodeType": "FunctionNode",
      "FunctionSignature": "DSCore.Color.ByARGB@int,int,int,int",
      "Id": "ae0f7c8e8cd24491bea17f6e8c83c6cd",
      "Inputs": [
        {
          "Id": "9ea1ea98c69d4eb286a5d603fda866f1",
          "Name": "a",
          "Description": "The alpha value.\n\nint\nDefault value : 255",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "cacf6f324848498daa60ae428376e90e",
          "Name": "r",
          "Description": "The red value.\n\nint\nDefault value : 0",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "534cde62ee0c4efc961ec968bb2d3876",
          "Name": "g",
          "Description": "The green value.\n\nint\nDefault value : 0",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        },
        {
          "Id": "a8d7bf5f56a344999263115e23d3efe8",
          "Name": "b",
          "Description": "The blue value.\n\nint\nDefault value : 0",
          "UsingDefaultValue": true,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Outputs": [
        {
          "Id": "296942596242496ba90791b81742ccf5",
          "Name": "color",
          "Description": "Color.",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Auto",
      "Description": "Construct a color by alpha, red, green, and blue components.\n\nColor.ByARGB (a: int = 255, r: int = 0, g: int = 0, b: int = 0): Color"
    },
    {
      "ConcreteType": "Dynamo.Graph.Nodes.CodeBlockNodeModel, DynamoCore",
      "NodeType": "CodeBlockNode",
      "Code": "255;",
      "Id": "720983923e874e0088d1cf560cdde282",
      "Inputs": [],
      "Outputs": [
        {
          "Id": "6363bf017e1b428daae76ad1fe7add27",
          "Name": "",
          "Description": "Value of expression at line 1",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Disabled",
      "Description": "Allows for DesignScript code to be authored directly"
    },
    {
      "ConcreteType": "Dynamo.Graph.Nodes.ZeroTouch.DSFunction, DynamoCore",
      "NodeType": "FunctionNode",
      "FunctionSignature": "DSCore.List.Transpose@var[]..[]",
      "Id": "d9b80611fbb94f8f80485807eaabd9f8",
      "Inputs": [
        {
          "Id": "c8c83d7e063047728bc5497e9c49d94b",
          "Name": "lists",
          "Description": "A list of lists to be transposed.\n\nvar[]..[]",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Outputs": [
        {
          "Id": "1e323e7d84a6424c9c889c537851e89a",
          "Name": "lists",
          "Description": "A list of transposed lists.",
          "UsingDefaultValue": false,
          "Level": 2,
          "UseLevels": false,
          "KeepListStructure": false
        }
      ],
      "Replication": "Auto",
      "Description": "Swaps rows and columns in a list of lists. If there are some rows that are shorter than others, null values are inserted as place holders in the resultant array such that it is always rectangular.\n\nList.Transpose (lists: var[]..[]): var[]..[]"
    }
  ],
  "Connectors": [
    {
      "Start": "060f926f03fe496da0d26dd4fc81c533",
      "End": "7b56da3191ff4a818e838a84ca2af523",
      "Id": "ed729cc9f0984e0babea60f0fc3545b1"
    },
    {
      "Start": "48a6335c8f9f441f8b6d0be0bc5646fa",
      "End": "bd70505e5091473eb1b716c043b5d86a",
      "Id": "85ab0aa522f241e49b68e2f7e89ddaec"
    },
    {
      "Start": "02c844015268477d965c0708c58fb086",
      "End": "81285b23c3de43e4a47139ed27870197",
      "Id": "15e59c686f6346058853d098436ef19e"
    },
    {
      "Start": "eef0aca7e50a44cd9642eddb4883834d",
      "End": "189bcb32aa7742ee9460e3e398062dba",
      "Id": "6d5d0c66bacf4af98bb183ae25b0b0b3"
    },
    {
      "Start": "eef0aca7e50a44cd9642eddb4883834d",
      "End": "53730bd2d414492fac8dac928fbda5c6",
      "Id": "a8fbfe0bff154bcfa7c66b239ae65e68"
    },
    {
      "Start": "c130e89bf8c34e3c8c4ecb24dfc14925",
      "End": "c68cd829dc2b4edaaf065db024f7ce7d",
      "Id": "ccc6614b692841c489ebde8520eeb0c6"
    },
    {
      "Start": "7fd1a6a827cf4515b322c9162c9e570d",
      "End": "be6b5a4f31944b02931c6b0aef12fdb7",
      "Id": "6bb048a5734a42ffabd60a853261b0f2"
    },
    {
      "Start": "c8a02d93936443c49fb910479799648d",
      "End": "287ade5fe56c4cc4995e81efd4391a89",
      "Id": "2b440a298aaf472ab1f8d91aa02bb97f"
    },
    {
      "Start": "9a01b59923584397bde514587188f470",
      "End": "51a4fac869c34fa28d932569f8220aa6",
      "Id": "607396a7ae5f4dcba101ea18f4110f46"
    },
    {
      "Start": "942779ba654f450b93ba6bcb1ee92e71",
      "End": "cb190eac18ab454aa0e6132d0d6e9c18",
      "Id": "32e3746475434b4b9626c9c9c2d21c58"
    },
    {
      "Start": "f0930982a3854191aae167611f435564",
      "End": "c604e18da96b4f6c8935a4b869d515a6",
      "Id": "a516cf0815da4b52b5bf35514f46ff17"
    },
    {
      "Start": "62a86696fb8d467e9f82a72573f70022",
      "End": "f9d34452abf04bbab084f07c6f7e3e82",
      "Id": "2005f4a90c5f4056b57db831daa76ff0"
    },
    {
      "Start": "2a22c768698b4fb4a73493666eb9cd34",
      "End": "d337346db5134358836469fb348914b0",
      "Id": "51dbdbaef171499085c3633cc1b06f63"
    },
    {
      "Start": "f30c7952eb0d417fb7e83491d255ff0f",
      "End": "5e783995dc334b5094d04375966a9a69",
      "Id": "51aba07d20804039a9e7cfb3cfb04adf"
    },
    {
      "Start": "1b1df20198c2462b8cb594c4ef414f18",
      "End": "c3134316008e445f8de449e30778de07",
      "Id": "f7ff7e2052ff459ba05f0c9064391c69"
    },
    {
      "Start": "1b1df20198c2462b8cb594c4ef414f18",
      "End": "c8c83d7e063047728bc5497e9c49d94b",
      "Id": "5686347f88dd4f4bbbdf23f4e12faacf"
    },
    {
      "Start": "f33fbfb05d2444f6a555821a34c80a81",
      "End": "ad65a0c5400a421db46f89cd726fb132",
      "Id": "4728e840eaa74a2cab4af01428258ee1"
    },
    {
      "Start": "7ea99569925d4a30a00c9f287c484e29",
      "End": "a59f8715d6b34a51beabfb63233dde96",
      "Id": "37340f7579954027b85de89db54a18ec"
    },
    {
      "Start": "6d8208ed3d434c4a99b565309d45eb98",
      "End": "0ead0e4e461e43528cbd8baf5266153a",
      "Id": "3ceaecfe3a1d496b94965e34ca41cf26"
    },
    {
      "Start": "fdf82c8d73554a84add39182a4525e3e",
      "End": "30a24438ea894c9ba72d84e8fa365954",
      "Id": "fc451d55717642a4a943e38b2eb74ff5"
    },
    {
      "Start": "6c961d5129b8468d9ed85e55fb8db7b0",
      "End": "1e040db4bf5b4887bb538c1f26477d14",
      "Id": "a02e5e8aad834f5491dd94c8c05a823e"
    },
    {
      "Start": "7f43ef4fe19b454c80a55a051b8f61a8",
      "End": "50749568ba574df49d036073d3111ee7",
      "Id": "8cf898aa441046c09834d1fff5792bfa"
    },
    {
      "Start": "296942596242496ba90791b81742ccf5",
      "End": "ecb7d1ef87774dc0a117f4df657fbdf5",
      "Id": "57e0c7151f194aa0bdbbedec59e18473"
    },
    {
      "Start": "6363bf017e1b428daae76ad1fe7add27",
      "End": "cacf6f324848498daa60ae428376e90e",
      "Id": "ac5616d8118a42b0a98da759958b560c"
    },
    {
      "Start": "1e323e7d84a6424c9c889c537851e89a",
      "End": "b60f1fd7f23a4624a2316fa0ef840d7b",
      "Id": "6905325784c44bb4af70b95b3fc958d1"
    }
  ],
  "Dependencies": [],
  "NodeLibraryDependencies": [],
  "Bindings": [
    {
      "NodeId": "132c8c0e-4841-4131-aa7c-8610ea89c7ef",
      "Binding": {
        "ByFloorPlanPoints_InClassDecl-1_InFunctionScope-1_Instance0_132c8c0e-4841-4131-aa7c-8610ea89c7ef": "PFNPQVAtRU5WOkVudmVsb3BlIHhtbG5zOnhzaT0iaHR0cDovL3d3dy53My5vcmcvMjAwMS9YTUxTY2hlbWEtaW5zdGFuY2UiIHhtbG5zOnhzZD0iaHR0cDovL3d3dy53My5vcmcvMjAwMS9YTUxTY2hlbWEiIHhtbG5zOlNPQVAtRU5DPSJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy9zb2FwL2VuY29kaW5nLyIgeG1sbnM6U09BUC1FTlY9Imh0dHA6Ly9zY2hlbWFzLnhtbHNvYXAub3JnL3NvYXAvZW52ZWxvcGUvIiB4bWxuczpjbHI9Imh0dHA6Ly9zY2hlbWFzLm1pY3Jvc29mdC5jb20vc29hcC9lbmNvZGluZy9jbHIvMS4wIiBTT0FQLUVOVjplbmNvZGluZ1N0eWxlPSJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy9zb2FwL2VuY29kaW5nLyI+DQo8U09BUC1FTlY6Qm9keT4NCjxhMTpDYWxsU2l0ZV94MDAyQl9UcmFjZVNlcmlhbGlzZXJIZWxwZXIgaWQ9InJlZi0xIiB4bWxuczphMT0iaHR0cDovL3NjaGVtYXMubWljcm9zb2Z0LmNvbS9jbHIvbnNhc3NlbS9Qcm90b0NvcmUvUHJvdG9Db3JlJTJDJTIwVmVyc2lvbiUzRDIuMy4wLjU4ODUlMkMlMjBDdWx0dXJlJTNEbmV1dHJhbCUyQyUyMFB1YmxpY0tleVRva2VuJTNEbnVsbCI+DQo8TnVtYmVyT2ZFbGVtZW50cz4xPC9OdW1iZXJPZkVsZW1lbnRzPg0KPEJhc2UtMF9IYXNEYXRhPmZhbHNlPC9CYXNlLTBfSGFzRGF0YT4NCjxCYXNlLTBfSGFzTmVzdGVkRGF0YT50cnVlPC9CYXNlLTBfSGFzTmVzdGVkRGF0YT4NCjxCYXNlLTBfTmVzdGVkRGF0YUNvdW50PjU8L0Jhc2UtMF9OZXN0ZWREYXRhQ291bnQ+DQo8QmFzZS0wLTBfSGFzRGF0YT5mYWxzZTwvQmFzZS0wLTBfSGFzRGF0YT4NCjxCYXNlLTAtMF9IYXNOZXN0ZWREYXRhPnRydWU8L0Jhc2UtMC0wX0hhc05lc3RlZERhdGE+DQo8QmFzZS0wLTBfTmVzdGVkRGF0YUNvdW50PjE8L0Jhc2UtMC0wX05lc3RlZERhdGFDb3VudD4NCjxCYXNlLTAtMC0wX0hhc0RhdGE+dHJ1ZTwvQmFzZS0wLTAtMF9IYXNEYXRhPg0KPEJhc2UtMC0wLTBfRGF0YSBpZD0icmVmLTMiPlBGTlBRVkF0UlU1V09rVnVkbVZzYjNCbElIaHRiRzV6T25oemFUMGlhSFIwY0RvdkwzZDNkeTUzTXk1dmNtY3ZNakF3TVM5WVRVeFRZMmhsYldFdGFXNXpkR0Z1WTJVaUlIaHRiRzV6T25oelpEMGlhSFIwY0RvdkwzZDNkeTUzTXk1dmNtY3ZNakF3TVM5WVRVeFRZMmhsYldFaUlIaHRiRzV6T2xOUFFWQXRSVTVEUFNKb2RIUndPaTh2YzJOb1pXMWhjeTU0Yld4emIyRndMbTl5Wnk5emIyRndMMlZ1WTI5a2FXNW5MeUlnZUcxc2JuTTZVMDlCVUMxRlRsWTlJbWgwZEhBNkx5OXpZMmhsYldGekxuaHRiSE52WVhBdWIzSm5MM052WVhBdlpXNTJaV3h2Y0dVdklpQjRiV3h1Y3pwamJISTlJbWgwZEhBNkx5OXpZMmhsYldGekxtMXBZM0p2YzI5bWRDNWpiMjB2YzI5aGNDOWxibU52WkdsdVp5OWpiSEl2TVM0d0lpQlRUMEZRTFVWT1ZqcGxibU52WkdsdVoxTjBlV3hsUFNKb2RIUndPaTh2YzJOb1pXMWhjeTU0Yld4emIyRndMbTl5Wnk5emIyRndMMlZ1WTI5a2FXNW5MeUkrRFFvOFUwOUJVQzFGVGxZNlFtOWtlVDROQ2p4aE1UcE5kV3gwYVhCc1pWTmxjbWxoYkdsNllXSnNaVWxrSUdsa1BTSnlaV1l0TVNJZ2VHMXNibk02WVRFOUltaDBkSEE2THk5elkyaGxiV0Z6TG0xcFkzSnZjMjltZEM1amIyMHZZMnh5TDI1ellYTnpaVzB2VW1WMmFYUlRaWEoyYVdObGN5NVFaWEp6YVhOMFpXNWpaUzlTWlhacGRGTmxjblpwWTJWekpUSkRKVEl3Vm1WeWMybHZiaVV6UkRJdU15NHdMall5TnpBbE1rTWxNakJEZFd4MGRYSmxKVE5FYm1WMWRISmhiQ1V5UXlVeU1GQjFZbXhwWTB0bGVWUnZhMlZ1SlRORWJuVnNiQ0krRFFvOGJuVnRZbVZ5VDJaRmJHVnRaVzUwY3o0eFBDOXVkVzFpWlhKUFprVnNaVzFsYm5SelBnMEtQSE4wY21sdVowbEVMVEFnYVdROUluSmxaaTB6SWo0d01USXhNekUxWVMwNVpUVTJMVFF6TXpFdE9URmtOaTFtWXpKbVpEQXlZbU13WkRjdE1EQTFORFkyT0RBOEwzTjBjbWx1WjBsRUxUQStEUW84YVc1MFNVUXRNRDQxTlRNeE1qWTBQQzlwYm5SSlJDMHdQZzBLUEM5aE1UcE5kV3gwYVhCc1pWTmxjbWxoYkdsNllXSnNaVWxrUGcwS1BDOVRUMEZRTFVWT1ZqcENiMlI1UGcwS1BDOVRUMEZRTFVWT1ZqcEZiblpsYkc5d1pUNE5DZz09PC9CYXNlLTAtMC0wX0RhdGE+DQo8QmFzZS0wLTAtMF9IYXNOZXN0ZWREYXRhPnRydWU8L0Jhc2UtMC0wLTBfSGFzTmVzdGVkRGF0YT4NCjxCYXNlLTAtMC0wX05lc3RlZERhdGFDb3VudD4xPC9CYXNlLTAtMC0wX05lc3RlZERhdGFDb3VudD4NCjxCYXNlLTAtMC0wLTBfSGFzRGF0YT5mYWxzZTwvQmFzZS0wLTAtMC0wX0hhc0RhdGE+DQo8QmFzZS0wLTAtMC0wX0hhc05lc3RlZERhdGE+ZmFsc2U8L0Jhc2UtMC0wLTAtMF9IYXNOZXN0ZWREYXRhPg0KPEJhc2UtMC0xX0hhc0RhdGE+ZmFsc2U8L0Jhc2UtMC0xX0hhc0RhdGE+DQo8QmFzZS0wLTFfSGFzTmVzdGVkRGF0YT50cnVlPC9CYXNlLTAtMV9IYXNOZXN0ZWREYXRhPg0KPEJhc2UtMC0xX05lc3RlZERhdGFDb3VudD4xPC9CYXNlLTAtMV9OZXN0ZWREYXRhQ291bnQ+DQo8QmFzZS0wLTEtMF9IYXNEYXRhPmZhbHNlPC9CYXNlLTAtMS0wX0hhc0RhdGE+DQo8QmFzZS0wLTEtMF9IYXNOZXN0ZWREYXRhPnRydWU8L0Jhc2UtMC0xLTBfSGFzTmVzdGVkRGF0YT4NCjxCYXNlLTAtMS0wX05lc3RlZERhdGFDb3VudD4xPC9CYXNlLTAtMS0wX05lc3RlZERhdGFDb3VudD4NCjxCYXNlLTAtMS0wLTBfSGFzRGF0YT5mYWxzZTwvQmFzZS0wLTEtMC0wX0hhc0RhdGE+DQo8QmFzZS0wLTEtMC0wX0hhc05lc3RlZERhdGE+ZmFsc2U8L0Jhc2UtMC0xLTAtMF9IYXNOZXN0ZWREYXRhPg0KPEJhc2UtMC0yX0hhc0RhdGE+ZmFsc2U8L0Jhc2UtMC0yX0hhc0RhdGE+DQo8QmFzZS0wLTJfSGFzTmVzdGVkRGF0YT50cnVlPC9CYXNlLTAtMl9IYXNOZXN0ZWREYXRhPg0KPEJhc2UtMC0yX05lc3RlZERhdGFDb3VudD4xPC9CYXNlLTAtMl9OZXN0ZWREYXRhQ291bnQ+DQo8QmFzZS0wLTItMF9IYXNEYXRhPmZhbHNlPC9CYXNlLTAtMi0wX0hhc0RhdGE+DQo8QmFzZS0wLTItMF9IYXNOZXN0ZWREYXRhPnRydWU8L0Jhc2UtMC0yLTBfSGFzTmVzdGVkRGF0YT4NCjxCYXNlLTAtMi0wX05lc3RlZERhdGFDb3VudD4xPC9CYXNlLTAtMi0wX05lc3RlZERhdGFDb3VudD4NCjxCYXNlLTAtMi0wLTBfSGFzRGF0YT5mYWxzZTwvQmFzZS0wLTItMC0wX0hhc0RhdGE+DQo8QmFzZS0wLTItMC0wX0hhc05lc3RlZERhdGE+ZmFsc2U8L0Jhc2UtMC0yLTAtMF9IYXNOZXN0ZWREYXRhPg0KPEJhc2UtMC0zX0hhc0RhdGE+ZmFsc2U8L0Jhc2UtMC0zX0hhc0RhdGE+DQo8QmFzZS0wLTNfSGFzTmVzdGVkRGF0YT50cnVlPC9CYXNlLTAtM19IYXNOZXN0ZWREYXRhPg0KPEJhc2UtMC0zX05lc3RlZERhdGFDb3VudD4xPC9CYXNlLTAtM19OZXN0ZWREYXRhQ291bnQ+DQo8QmFzZS0wLTMtMF9IYXNEYXRhPmZhbHNlPC9CYXNlLTAtMy0wX0hhc0RhdGE+DQo8QmFzZS0wLTMtMF9IYXNOZXN0ZWREYXRhPnRydWU8L0Jhc2UtMC0zLTBfSGFzTmVzdGVkRGF0YT4NCjxCYXNlLTAtMy0wX05lc3RlZERhdGFDb3VudD4xPC9CYXNlLTAtMy0wX05lc3RlZERhdGFDb3VudD4NCjxCYXNlLTAtMy0wLTBfSGFzRGF0YT5mYWxzZTwvQmFzZS0wLTMtMC0wX0hhc0RhdGE+DQo8QmFzZS0wLTMtMC0wX0hhc05lc3RlZERhdGE+ZmFsc2U8L0Jhc2UtMC0zLTAtMF9IYXNOZXN0ZWREYXRhPg0KPEJhc2UtMC00X0hhc0RhdGE+ZmFsc2U8L0Jhc2UtMC00X0hhc0RhdGE+DQo8QmFzZS0wLTRfSGFzTmVzdGVkRGF0YT50cnVlPC9CYXNlLTAtNF9IYXNOZXN0ZWREYXRhPg0KPEJhc2UtMC00X05lc3RlZERhdGFDb3VudD4xPC9CYXNlLTAtNF9OZXN0ZWREYXRhQ291bnQ+DQo8QmFzZS0wLTQtMF9IYXNEYXRhPnRydWU8L0Jhc2UtMC00LTBfSGFzRGF0YT4NCjxCYXNlLTAtNC0wX0RhdGEgaWQ9InJlZi00Ij5QRk5QUVZBdFJVNVdPa1Z1ZG1Wc2IzQmxJSGh0Ykc1ek9uaHphVDBpYUhSMGNEb3ZMM2QzZHk1M015NXZjbWN2TWpBd01TOVlUVXhUWTJobGJXRXRhVzV6ZEdGdVkyVWlJSGh0Ykc1ek9uaHpaRDBpYUhSMGNEb3ZMM2QzZHk1M015NXZjbWN2TWpBd01TOVlUVXhUWTJobGJXRWlJSGh0Ykc1ek9sTlBRVkF0UlU1RFBTSm9kSFJ3T2k4dmMyTm9aVzFoY3k1NGJXeHpiMkZ3TG05eVp5OXpiMkZ3TDJWdVkyOWthVzVuTHlJZ2VHMXNibk02VTA5QlVDMUZUbFk5SW1oMGRIQTZMeTl6WTJobGJXRnpMbmh0YkhOdllYQXViM0puTDNOdllYQXZaVzUyWld4dmNHVXZJaUI0Yld4dWN6cGpiSEk5SW1oMGRIQTZMeTl6WTJobGJXRnpMbTFwWTNKdmMyOW1kQzVqYjIwdmMyOWhjQzlsYm1OdlpHbHVaeTlqYkhJdk1TNHdJaUJUVDBGUUxVVk9WanBsYm1OdlpHbHVaMU4wZVd4bFBTSm9kSFJ3T2k4dmMyTm9aVzFoY3k1NGJXeHpiMkZ3TG05eVp5OXpiMkZ3TDJWdVkyOWthVzVuTHlJK0RRbzhVMDlCVUMxRlRsWTZRbTlrZVQ0TkNqeGhNVHBOZFd4MGFYQnNaVk5sY21saGJHbDZZV0pzWlVsa0lHbGtQU0p5WldZdE1TSWdlRzFzYm5NNllURTlJbWgwZEhBNkx5OXpZMmhsYldGekxtMXBZM0p2YzI5bWRDNWpiMjB2WTJ4eUwyNXpZWE56WlcwdlVtVjJhWFJUWlhKMmFXTmxjeTVRWlhKemFYTjBaVzVqWlM5U1pYWnBkRk5sY25acFkyVnpKVEpESlRJd1ZtVnljMmx2YmlVelJESXVNeTR3TGpZeU56QWxNa01sTWpCRGRXeDBkWEpsSlRORWJtVjFkSEpoYkNVeVF5VXlNRkIxWW14cFkwdGxlVlJ2YTJWdUpUTkViblZzYkNJK0RRbzhiblZ0WW1WeVQyWkZiR1Z0Wlc1MGN6NHhQQzl1ZFcxaVpYSlBaa1ZzWlcxbGJuUnpQZzBLUEhOMGNtbHVaMGxFTFRBZ2FXUTlJbkpsWmkweklqNHdNVEl4TXpFMVlTMDVaVFUyTFRRek16RXRPVEZrTmkxbVl6Sm1aREF5WW1Nd1pEY3RNREExTkRZMk9ERThMM04wY21sdVowbEVMVEErRFFvOGFXNTBTVVF0TUQ0MU5UTXhNalkxUEM5cGJuUkpSQzB3UGcwS1BDOWhNVHBOZFd4MGFYQnNaVk5sY21saGJHbDZZV0pzWlVsa1BnMEtQQzlUVDBGUUxVVk9WanBDYjJSNVBnMEtQQzlUVDBGUUxVVk9WanBGYm5abGJHOXdaVDROQ2c9PTwvQmFzZS0wLTQtMF9EYXRhPg0KPEJhc2UtMC00LTBfSGFzTmVzdGVkRGF0YT50cnVlPC9CYXNlLTAtNC0wX0hhc05lc3RlZERhdGE+DQo8QmFzZS0wLTQtMF9OZXN0ZWREYXRhQ291bnQ+MTwvQmFzZS0wLTQtMF9OZXN0ZWREYXRhQ291bnQ+DQo8QmFzZS0wLTQtMC0wX0hhc0RhdGE+ZmFsc2U8L0Jhc2UtMC00LTAtMF9IYXNEYXRhPg0KPEJhc2UtMC00LTAtMF9IYXNOZXN0ZWREYXRhPmZhbHNlPC9CYXNlLTAtNC0wLTBfSGFzTmVzdGVkRGF0YT4NCjwvYTE6Q2FsbFNpdGVfeDAwMkJfVHJhY2VTZXJpYWxpc2VySGVscGVyPg0KPC9TT0FQLUVOVjpCb2R5Pg0KPC9TT0FQLUVOVjpFbnZlbG9wZT4NCg=="
      }
    }
  ],
  "View": {
    "Dynamo": {
      "ScaleFactor": 1.0,
      "HasRunWithoutCrash": true,
      "IsVisibleInDynamoLibrary": true,
      "Version": "2.3.0.5885",
      "RunType": "Manual",
      "RunPeriod": "1000"
    },
    "Camera": {
      "Name": "Background Preview",
      "EyeX": 2681.1471361093227,
      "EyeY": 1501.7298955653189,
      "EyeZ": 8494.7573475422651,
      "LookX": 1567.4919200429363,
      "LookY": -1698.116246713181,
      "LookZ": -7576.210946874191,
      "UpX": 0.0,
      "UpY": 1.0,
      "UpZ": 0.0
    },
    "NodeViews": [
      {
        "ShowGeometry": true,
        "Name": "PathOfTravel.ByFloorPlanPoints",
        "Id": "132c8c0e48414131aa7c8610ea89c7ef",
        "IsSetAsInput": false,
        "IsSetAsOutput": true,
        "Excluded": false,
        "X": 1299.8547843599601,
        "Y": 38.627651461188236
      },
      {
        "ShowGeometry": true,
        "Name": "Boolean",
        "Id": "436919e9a2ca40fc9ed3bb97a4df5201",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 945.83264094955473,
        "Y": 719.72225519287861
      },
      {
        "ShowGeometry": true,
        "Name": "Room.Location",
        "Id": "a886a0d815394701863b8c69ff608ea6",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 585.1367777419415,
        "Y": -127.29296539952844
      },
      {
        "ShowGeometry": true,
        "Name": "All Elements of Category",
        "Id": "446d42b1aa0b4328af61c6378d4718f6",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 274.5117672191526,
        "Y": -37.400428022478195
      },
      {
        "ShowGeometry": true,
        "Name": "Categories",
        "Id": "98384bab1e9e4022b26f2205ea17a702",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": -27.424261162499192,
        "Y": -21.667299694079503
      },
      {
        "ShowGeometry": true,
        "Name": "List.Clean",
        "Id": "72dac09e434d4b9ca497aaac1b8d6cf9",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 871.17164876253207,
        "Y": 60.764127431708062
      },
      {
        "ShowGeometry": true,
        "Name": "Boolean",
        "Id": "8c5d02115d324e97a46b528e1cea6bfa",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 649.3991589304834,
        "Y": 174.62845717206034
      },
      {
        "ShowGeometry": true,
        "Name": "Select Model Element",
        "Id": "b57c2682f6b3412281bf06104f1a8767",
        "IsSetAsInput": true,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 373.17507418397645,
        "Y": 612.46290801186933
      },
      {
        "ShowGeometry": true,
        "Name": "Element.GetLocation",
        "Id": "7af791e506d1467488b1a073e268862b",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 627.28974387361347,
        "Y": 505.25217738259596
      },
      {
        "ShowGeometry": true,
        "Name": "Views",
        "Id": "beeb9cc8de98440aa883bd081bfbae18",
        "IsSetAsInput": true,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 1026.3469447511147,
        "Y": -90.32163371467206
      },
      {
        "ShowGeometry": true,
        "Name": "List Create",
        "Id": "a7c8df3fa8d3434796c3a1a58a48ea3a",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 878.5964764881852,
        "Y": 368.45032403625828
      },
      {
        "ShowGeometry": true,
        "Name": "Room.Name",
        "Id": "d075f88152e64da4a9bc4a1c57e89d48",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 528.58736864213529,
        "Y": -243.93945138357617
      },
      {
        "ShowGeometry": true,
        "Name": "Element.GetParameterValueByName",
        "Id": "d554667e496848248680d415ccd4ace7",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 2226.5705081987048,
        "Y": 76.009770756751152
      },
      {
        "ShowGeometry": true,
        "Name": "String",
        "Id": "38e607ea3af044f4a0ec69bc707742da",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 1706.1027633068857,
        "Y": 188.73339975816396
      },
      {
        "ShowGeometry": true,
        "Name": "List.Clean",
        "Id": "3136b1340c3a46509e61bd27ced517b1",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 1735.3941248315309,
        "Y": -132.34423279905843
      },
      {
        "ShowGeometry": true,
        "Name": "Boolean",
        "Id": "ce176f7fb4d74cd1a96443ac18aa7d33",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 1632.3038787000273,
        "Y": 95.857147690969668
      },
      {
        "ShowGeometry": true,
        "Name": "Element.OverrideInView",
        "Id": "4a5f0fdca88e40ac95cd866b1f945dc2",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 4129.4778537734719,
        "Y": -171.90346533078633
      },
      {
        "ShowGeometry": true,
        "Name": ">",
        "Id": "6490c4bbffc944aa98677323d13b19a9",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 2572.38134176096,
        "Y": 89.095587050276265
      },
      {
        "ShowGeometry": true,
        "Name": "Code Block",
        "Id": "a859ab6891b64a4192bb3dcc0dd627a9",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 2446.2170849295644,
        "Y": 264.67398209233238
      },
      {
        "ShowGeometry": true,
        "Name": "List.FilterByBoolMask",
        "Id": "56996316836e4c62a83ceaf0a3091dd9",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 3145.1316916473397,
        "Y": -80.210571746370988
      },
      {
        "ShowGeometry": true,
        "Name": "List.Transpose",
        "Id": "ed2ac9548d834b2f809801fc78bd1ecf",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 2822.4998789266692,
        "Y": 172.41734304345732
      },
      {
        "ShowGeometry": true,
        "Name": "OverrideGraphicSettings.ByProperties",
        "Id": "5831251f0b3445b1ba0c77462a1c6b5c",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 3807.750038866955,
        "Y": 75.715468850612865
      },
      {
        "ShowGeometry": true,
        "Name": "Color.ByARGB",
        "Id": "ae0f7c8e8cd24491bea17f6e8c83c6cd",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 3612.2595378346036,
        "Y": 186.01515521290241
      },
      {
        "ShowGeometry": true,
        "Name": "Code Block",
        "Id": "720983923e874e0088d1cf560cdde282",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 3473.0,
        "Y": 235.81021408652202
      },
      {
        "ShowGeometry": true,
        "Name": "List.Transpose",
        "Id": "d9b80611fbb94f8f80485807eaabd9f8",
        "IsSetAsInput": false,
        "IsSetAsOutput": false,
        "Excluded": false,
        "X": 2348.3342183932218,
        "Y": -83.1960584910396
      }
    ],
    "Annotations": [],
    "X": -1311.5075821798307,
    "Y": 180.92350356615276,
    "Zoom": 0.45927211895719672
  }
}
