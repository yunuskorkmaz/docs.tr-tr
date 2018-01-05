---
title: "LINQ to nesneleri etkinliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 403c82e8-7f2b-42f6-93cd-95c35bc76ead
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff77211000cfdda9c35e5a0dcbc69fc0eaf5c3be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-objects-activity"></a><span data-ttu-id="13b2f-102">LINQ to nesneleri etkinliği</span><span class="sxs-lookup"><span data-stu-id="13b2f-102">LINQ to Objects Activity</span></span>
<span data-ttu-id="13b2f-103">Bu örnek, bir koleksiyon sorgu öğelerine nesnelere LINQ kullanmak için bir etkinlik oluşturmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="13b2f-103">This sample demonstrates how to create an activity to use LINQ to Objects to query elements in a collection.</span></span>  
  
## <a name="activity-details-for-findincollection"></a><span data-ttu-id="13b2f-104">FindInCollection etkinliği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="13b2f-104">Activity Details for FindInCollection</span></span>  
 <span data-ttu-id="13b2f-105">Bu etkinlik kullanıcılar sorgu öğelerine nesnelere LINQ kullanarak bellek koleksiyonlarında izin verir.</span><span class="sxs-lookup"><span data-stu-id="13b2f-105">This activity allows users to query elements from collections in memory using LINQ to Objects.</span></span> <span data-ttu-id="13b2f-106">Sonuçları filtrelemek için bir lambda ifadesi şeklinde LINQ koşulu sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="13b2f-106">You must provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="13b2f-107">Bu etkinliği ile birlikte kullanılabilir <xref:System.Activities.Statements.AddToCollection%601> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="13b2f-107">This activity can be used in conjunction with <xref:System.Activities.Statements.AddToCollection%601> activities.</span></span>  
  
 <span data-ttu-id="13b2f-108">Aşağıdaki tabloda özellik ve dönüş değerleri etkinliğinin ayrıntılarını verir.</span><span class="sxs-lookup"><span data-stu-id="13b2f-108">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="13b2f-109">Özellik veya dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="13b2f-109">Property or Return Value</span></span>|<span data-ttu-id="13b2f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13b2f-110">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="13b2f-111">`Collection`özelliği</span><span class="sxs-lookup"><span data-stu-id="13b2f-111">`Collection` property</span></span>|<span data-ttu-id="13b2f-112">Kaynak koleksiyonu belirten gerekli bir özellik.</span><span class="sxs-lookup"><span data-stu-id="13b2f-112">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="13b2f-113">`Predicate`özelliği</span><span class="sxs-lookup"><span data-stu-id="13b2f-113">`Predicate` property</span></span>|<span data-ttu-id="13b2f-114">Filtre koleksiyonu için bir lambda ifadesi biçiminde belirtir gerekli bir özellik.</span><span class="sxs-lookup"><span data-stu-id="13b2f-114">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="13b2f-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13b2f-115">Return Value</span></span>|<span data-ttu-id="13b2f-116">Filtrelenmiş koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="13b2f-116">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="13b2f-117">Özel Etkinlik kullanan örnek kod</span><span class="sxs-lookup"><span data-stu-id="13b2f-117">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="13b2f-118">Aşağıdaki kod örneğinde `FindInCollection` olan çalışanlar bir koleksiyondaki tüm satırları bulmak için özel etkinlik bir `Role` özelliğini `Manager` ve `Location` özelliğini `Redmond`.</span><span class="sxs-lookup"><span data-stu-id="13b2f-118">The following code example uses the `FindInCollection` custom activity to find all rows in a collection of employees that have a `Role` property set to `Manager` and the `Location` property set to `Redmond`.</span></span>  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 <span data-ttu-id="13b2f-119">Aşağıdaki kod özel FindInCollection etkinliği kullanan bir iş akışı programı oluşturmak nasıl gösterir <xref:System.Activities.Statements.AddToCollection%601>, ve <xref:System.Activities.Statements.ForEach%601> çalışanlar, koleksiyonuyla doldurmak için etkinlikler Geliştirici rolleri ve bulunan tüm çalışanlar Bul Redmond ve sonuçta elde edilen listede yineleme.</span><span class="sxs-lookup"><span data-stu-id="13b2f-119">The following code shows how to create a workflow program that uses the custom FindInCollection activity, <xref:System.Activities.Statements.AddToCollection%601>, and <xref:System.Activities.Statements.ForEach%601> activities to populate a collection with employees, find all the employees that have developer roles and are located in Redmond, and then iterate through the resulting list.</span></span>  
  
```csharp  
// Create the Linq predicate for the find expression  
  
Func<Employee, bool> predicate = e => e.Role == "DEV" && e.Location.Equals("Redmond");  
  
// Create workflow program  
Activity sampleWorkflow = new Sequence  
{  
    Variables = { employees, devsFromRedmond },  
    Activities =  
    {  
        new Assign<IList<Employee>>  
        {  
            To = employees,  
            Value = new LambdaValue<IList<Employee>>(c => new List<Employee>())  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(1, "Employee 1", "DEV", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(2, "Employee 2", "DEV", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(3, "Employee 3", "PM", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(4, "Employee 4", "PM", "China"))  
        },  
        new FindInCollection<Employee>  
        {  
            Collections = new InArgument<IEnumerable<Employee>>(employees),  
            Predicate = new LambdaValue<Func<Employee, bool>>(c => predicate),  
            Result = new OutArgument<IList<Employee>>(devsFromRedmond)  
        },  
        new ForEach<Employee>  
        {  
            Values = new InArgument<IEnumerable<Employee>>(devsFromRedmond),  
            Body = new ActivityAction<Employee>  
            {  
                Argument = iterationVariable,  
                Handler = new WriteLine  
                {  
                    Text = new InArgument<string>(env => iterationVariable.Get(env).ToString())  
                }  
            }  
        }  
    }  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="13b2f-120">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="13b2f-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="13b2f-121">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], LinqToObjects.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="13b2f-121">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToObjects.sln solution file.</span></span>  
  
2.  <span data-ttu-id="13b2f-122">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="13b2f-122">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="13b2f-123">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="13b2f-123">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="13b2f-124">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="13b2f-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="13b2f-125">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="13b2f-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="13b2f-126">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="13b2f-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="13b2f-127">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="13b2f-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a><span data-ttu-id="13b2f-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13b2f-128">See Also</span></span>  
 [<span data-ttu-id="13b2f-129">Lambda ifadeleri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="13b2f-129">Lambda Expressions (C# Programming Guide)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150381)  
 [<span data-ttu-id="13b2f-130">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="13b2f-130">LINQ to Objects</span></span>](http://go.microsoft.com/fwlink/?LinkID=150380)
