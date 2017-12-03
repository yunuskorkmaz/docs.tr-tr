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
ms.openlocfilehash: 811ffe44a65dea13482d600a09989ce42f6580dd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="linq-to-objects-activity"></a>LINQ to nesneleri etkinliği
Bu örnek, bir koleksiyon sorgu öğelerine nesnelere LINQ kullanmak için bir etkinlik oluşturmak gösterilmiştir.  
  
## <a name="activity-details-for-findincollection"></a>FindInCollection etkinliği ayrıntıları  
 Bu etkinlik kullanıcılar sorgu öğelerine nesnelere LINQ kullanarak bellek koleksiyonlarında izin verir. Sonuçları filtrelemek için bir lambda ifadesi şeklinde LINQ koşulu sağlamanız gerekir. Bu etkinliği ile birlikte kullanılabilir <xref:System.Activities.Statements.AddToCollection%601> etkinlikler.  
  
 Aşağıdaki tabloda özellik ve dönüş değerleri etkinliğinin ayrıntılarını verir.  
  
|Özellik veya dönüş değeri|Açıklama|  
|------------------------------|-----------------|  
|`Collection`özelliği|Kaynak koleksiyonu belirten gerekli bir özellik.|  
|`Predicate`özelliği|Filtre koleksiyonu için bir lambda ifadesi biçiminde belirtir gerekli bir özellik.|  
|Dönüş Değeri|Filtrelenmiş koleksiyonu.|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a>Özel Etkinlik kullanan örnek kod  
 Aşağıdaki kod örneğinde `FindInCollection` olan çalışanlar bir koleksiyondaki tüm satırları bulmak için özel etkinlik bir `Role` özelliğini `Manager` ve `Location` özelliğini `Redmond`.  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 Aşağıdaki kod özel FindInCollection etkinliği kullanan bir iş akışı programı oluşturmak nasıl gösterir <xref:System.Activities.Statements.AddToCollection%601>, ve <xref:System.Activities.Statements.ForEach%601> çalışanlar, koleksiyonuyla doldurmak için etkinlikler Geliştirici rolleri ve bulunan tüm çalışanlar Bul Redmond ve sonuçta elde edilen listede yineleme.  
  
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
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], LinqToObjects.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Lambda ifadeleri (C# programlama Kılavuzu)](http://go.microsoft.com/fwlink/?LinkId=150381)  
 [Nesnelere LINQ](http://go.microsoft.com/fwlink/?LinkID=150380)
