---
title: LINQ to Objects etkinliği
ms.date: 03/30/2017
ms.assetid: 403c82e8-7f2b-42f6-93cd-95c35bc76ead
ms.openlocfilehash: fca4a94a951c9713a61914de6ef33e0cbb74f75e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552774"
---
# <a name="linq-to-objects-activity"></a>LINQ to Objects etkinliği
Bu örnek, bir koleksiyondaki sorgu öğeleri için LINQ to Objects'in kullanılacak bir etkinliği oluşturma işlemini gösterir.  
  
## <a name="activity-details-for-findincollection"></a>FindInCollection için etkinlik ayrıntıları  
 Bu etkinlik, kullanıcıların koleksiyonlarına kullanarak LINQ to Objects'in bellek içinde sorgu öğeleri sağlar. Sonuçları filtrelemek için bir lambda ifadesinin biçiminde bir LINQ koşul sağlamanız gerekir. Bu etkinlik ile birlikte kullanılabilir <xref:System.Activities.Statements.AddToCollection%601> etkinlikler.  
  
 Aşağıdaki tabloda özellik ve dönüş değerleri etkinliğinin ayrıntıları.  
  
|Özellik ya da dönüş değeri|Açıklama|  
|------------------------------|-----------------|  
|`Collection` Özelliği|Kaynak koleksiyonu belirtir. gerekli bir özellik.|  
|`Predicate` Özelliği|Filtre koleksiyonu için bir lambda ifadesinin biçiminde belirtir. gerekli bir özellik.|  
|Dönüş Değeri|Filtrelenmiş koleksiyonu.|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a>Özel Etkinlik kullanan kod örneği  
 Aşağıdaki kod örneğinde `FindInCollection` tüm satırları sahip çalışan bir koleksiyonda bulunacak özel etkinlik bir `Role` özelliğini `Manager` ve `Location` özelliğini `Redmond`.  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 Aşağıdaki kod, özel FindInCollection etkinliğini kullanan bir iş akışı program oluşturma işlemi gösterilmektedir <xref:System.Activities.Statements.AddToCollection%601>, ve <xref:System.Activities.Statements.ForEach%601> çalışanlar ile bir koleksiyon doldurmak için etkinlikleri bulmanıza Geliştirici rolleri ve bulunan tüm çalışanlar Redmond ve sonra elde edilen listede tekrarlayabilirsiniz.  
  
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
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Lambda ifadeleri (C# programlama Kılavuzu)](https://go.microsoft.com/fwlink/?LinkId=150381)  
 [LINQ to Objects](https://go.microsoft.com/fwlink/?LinkID=150380)
