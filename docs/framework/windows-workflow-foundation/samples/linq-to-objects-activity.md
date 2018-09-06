---
title: LINQ to Objects etkinliği
ms.date: 03/30/2017
ms.assetid: 403c82e8-7f2b-42f6-93cd-95c35bc76ead
ms.openlocfilehash: fca4a94a951c9713a61914de6ef33e0cbb74f75e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891586"
---
# <a name="linq-to-objects-activity"></a><span data-ttu-id="81598-102">LINQ to Objects etkinliği</span><span class="sxs-lookup"><span data-stu-id="81598-102">LINQ to Objects Activity</span></span>
<span data-ttu-id="81598-103">Bu örnek, bir koleksiyondaki sorgu öğeleri için LINQ to Objects'in kullanılacak bir etkinliği oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="81598-103">This sample demonstrates how to create an activity to use LINQ to Objects to query elements in a collection.</span></span>  
  
## <a name="activity-details-for-findincollection"></a><span data-ttu-id="81598-104">FindInCollection için etkinlik ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="81598-104">Activity Details for FindInCollection</span></span>  
 <span data-ttu-id="81598-105">Bu etkinlik, kullanıcıların koleksiyonlarına kullanarak LINQ to Objects'in bellek içinde sorgu öğeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="81598-105">This activity allows users to query elements from collections in memory using LINQ to Objects.</span></span> <span data-ttu-id="81598-106">Sonuçları filtrelemek için bir lambda ifadesinin biçiminde bir LINQ koşul sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="81598-106">You must provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="81598-107">Bu etkinlik ile birlikte kullanılabilir <xref:System.Activities.Statements.AddToCollection%601> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="81598-107">This activity can be used in conjunction with <xref:System.Activities.Statements.AddToCollection%601> activities.</span></span>  
  
 <span data-ttu-id="81598-108">Aşağıdaki tabloda özellik ve dönüş değerleri etkinliğinin ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="81598-108">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="81598-109">Özellik ya da dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="81598-109">Property or Return Value</span></span>|<span data-ttu-id="81598-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81598-110">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="81598-111">`Collection` Özelliği</span><span class="sxs-lookup"><span data-stu-id="81598-111">`Collection` property</span></span>|<span data-ttu-id="81598-112">Kaynak koleksiyonu belirtir. gerekli bir özellik.</span><span class="sxs-lookup"><span data-stu-id="81598-112">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="81598-113">`Predicate` Özelliği</span><span class="sxs-lookup"><span data-stu-id="81598-113">`Predicate` property</span></span>|<span data-ttu-id="81598-114">Filtre koleksiyonu için bir lambda ifadesinin biçiminde belirtir. gerekli bir özellik.</span><span class="sxs-lookup"><span data-stu-id="81598-114">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="81598-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="81598-115">Return Value</span></span>|<span data-ttu-id="81598-116">Filtrelenmiş koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="81598-116">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="81598-117">Özel Etkinlik kullanan kod örneği</span><span class="sxs-lookup"><span data-stu-id="81598-117">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="81598-118">Aşağıdaki kod örneğinde `FindInCollection` tüm satırları sahip çalışan bir koleksiyonda bulunacak özel etkinlik bir `Role` özelliğini `Manager` ve `Location` özelliğini `Redmond`.</span><span class="sxs-lookup"><span data-stu-id="81598-118">The following code example uses the `FindInCollection` custom activity to find all rows in a collection of employees that have a `Role` property set to `Manager` and the `Location` property set to `Redmond`.</span></span>  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 <span data-ttu-id="81598-119">Aşağıdaki kod, özel FindInCollection etkinliğini kullanan bir iş akışı program oluşturma işlemi gösterilmektedir <xref:System.Activities.Statements.AddToCollection%601>, ve <xref:System.Activities.Statements.ForEach%601> çalışanlar ile bir koleksiyon doldurmak için etkinlikleri bulmanıza Geliştirici rolleri ve bulunan tüm çalışanlar Redmond ve sonra elde edilen listede tekrarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81598-119">The following code shows how to create a workflow program that uses the custom FindInCollection activity, <xref:System.Activities.Statements.AddToCollection%601>, and <xref:System.Activities.Statements.ForEach%601> activities to populate a collection with employees, find all the employees that have developer roles and are located in Redmond, and then iterate through the resulting list.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="81598-120">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="81598-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="81598-121">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], LinqToObjects.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="81598-121">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToObjects.sln solution file.</span></span>  
  
2.  <span data-ttu-id="81598-122">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="81598-122">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="81598-123">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="81598-123">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="81598-124">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="81598-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="81598-125">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="81598-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="81598-126">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="81598-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="81598-127">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="81598-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a><span data-ttu-id="81598-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81598-128">See Also</span></span>  
 [<span data-ttu-id="81598-129">Lambda ifadeleri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="81598-129">Lambda Expressions (C# Programming Guide)</span></span>](https://go.microsoft.com/fwlink/?LinkId=150381)  
 [<span data-ttu-id="81598-130">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="81598-130">LINQ to Objects</span></span>](https://go.microsoft.com/fwlink/?LinkID=150380)
