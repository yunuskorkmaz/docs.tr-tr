---
title: DynamicActivity oluşturma
ms.date: 03/30/2017
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
ms.openlocfilehash: 270066fafd5c71b2a720ca305433159c172872aa
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777493"
---
# <a name="dynamicactivity-creation"></a>DynamicActivity oluşturma
Bu örnek, çalışma zamanı kullanarak bir etkinlik oluşturmak için iki farklı yol gösterir. <xref:System.Activities.DynamicActivity> etkinlik.  
  
 Bu örnekte, bir etkinlik içeren bir gövde ile çalışma zamanında oluşturulan bir <xref:System.Activities.Statements.Sequence> içeren etkinlik <xref:System.Activities.Statements.ForEach%601> ve <xref:System.Activities.Statements.Assign%601> etkinlikler. Giriş bir tamsayı listesi etkinliğini geçirilen ve bir özellik olarak ayarlayın. <xref:System.Activities.Statements.ForEach%601> Etkinliği ardından değerleri listesi yinelenir ve onu toplanır. İçinde <xref:System.Activities.Statements.Assign%601> etkinlik, ortalama değer listesindeki öğelerin sayısını accumulator bölünerek hesaplanır ve ortalama olarak atayın.  
  
 Örnek, kullanımını gösterir. bir <xref:System.Activities.DynamicActivity> çıktı bağımsız değişkenlerinde giriş bağımsız değişkenleri ve değerler olarak döndüren olarak akış etkinliği. Adlı bir giriş bağımsız değişkeni etkinliğinde `Numbers` tamsayı olan bir listesi. <xref:System.Activities.Statements.ForEach%601> Etkinliği değerleri listesi yinelenir ve onu toplanır. İçinde <xref:System.Activities.Statements.Assign%601> accumulator listedeki öğelerin sayısına göre bölme ve ortalama olarak atayarak etkinlik, ortalama değer hesaplanır. Ortalama adlı çıktı bağımsız değişken olarak döndürülen `Average`.  
  
 Zvolit dynamickou programlı bir şekilde oluşturulduğunda, giriş ve çıkış aşağıdaki kod örneğinde gösterildiği gibi bildirilir.  
  
```csharp  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
};  
```  
  
 Aşağıdaki kod örneği eksiksiz tanımını gösterir `DynamicActivity` , listedeki değerlerin ortalamasını hesaplar.  
  
```  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
    Implementation = () =>  
        new Sequence  
        {  
            Variables = { result, accumulator },  
            Activities =  
            {  
                new ForEach<int>  
                {  
                    Values =  new ArgumentValue<IEnumerable<int>> { ArgumentName = "Numbers" },                                  
                    Body = new ActivityAction<int>  
                    {  
                        Argument = iterationVariable,  
                        Handler = new Assign<int>  
                        {  
                            To = accumulator,  
                            Value = new InArgument<int>(env => iterationVariable.Get(env) +  accumulator.Get(env))  
                        }  
                    }  
                },  
  
                // Calculate the average and assign to the output argument.  
                new Assign<double>  
                {  
                    To = new ArgumentReference<double> { ArgumentName = "Average" },  
                    Value = new InArgument<double>(env => accumulator.Get(env) / numbers.Get(env).Count<int>())  
                },  
            }  
        }  
};  
```  
  
 XAML içinde oluştururken, giriş ve çıkış aşağıdaki örnekte gösterildiği gibi bildirilir.  
  
```xml  
<Activity x:Class="Microsoft.Samples.DynamicActivityCreation.FindAverage"  
          xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
          xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <x:Members>  
    <x:Property Name="Numbers" Type="InArgument(scg:List(x:Int32))" />  
    <x:Property Name="Average" Type="OutArgument(x:Double)" />  
  </x:Members>  
    ...  
    ...  
</Activity>  
```  
  
 XAML görsel olarak kullanılarak oluşturulabilir. [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]. Visual Studio projesi içinde yer alıyorsa "Derleme Eylemi'ni önlemek için Eylem" için "None" ayarladığınızdan emin olun. XAML, ardından aşağıdaki çağrı kullanılarak dinamik olarak yüklenebilir.  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 <xref:System.Activities.DynamicActivity> Örneği oluşturulan programlı olarak veya bir XAML yüklenirken aracılığıyla iş akışı aşağıdaki kod örneğinde gösterildiği gibi kullanılabilir. "İşlem" geçirilen olduğunu lütfen unutmayın `WorkflowInvoker.Invoke` "işlemidir" <xref:System.Activities.Activity> ilk kod örneğinde tanımlanan.  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], DynamicActivityCreation.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
## <a name="command-line-arguments"></a>Komut satırı bağımsız değişkenleri  
 Bu örnek, komut satırı bağımsız değişkenlerini kabul eder. Kullanıcılar kendi ortalamayı hesaplamak için etkinliğin sayıdan oluşan bir liste sağlar. Kullanılacak sayı listesi boşlukla ayırarak sayıdan oluşan bir liste olarak geçirilir. Örneğin, hesaplamak için ortalama 5, 10 ve 32 çağırma şu komut satırını kullanarak örneği.  
  
 **DynamicActivityCreation 5 10 32**  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`