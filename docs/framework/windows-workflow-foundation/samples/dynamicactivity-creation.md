---
title: "DynamicActivity oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4a579606bd3ee9d3f11669d59c6e7c9767b6eaf4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="dynamicactivity-creation"></a><span data-ttu-id="dc11b-102">DynamicActivity oluşturma</span><span class="sxs-lookup"><span data-stu-id="dc11b-102">DynamicActivity Creation</span></span>
<span data-ttu-id="dc11b-103">Bu örnek çalışma zamanı kullanarak bir etkinlik oluşturmak için iki farklı yolu gösterilmektedir <xref:System.Activities.DynamicActivity> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="dc11b-103">This sample demonstrates two different ways to create an activity at runtime using the <xref:System.Activities.DynamicActivity> activity.</span></span>  
  
 <span data-ttu-id="dc11b-104">Bu örnekte, bir etkinlik içeren bir gövde ile çalışma zamanında oluşturulan bir <xref:System.Activities.Statements.Sequence> içeren etkinlik <xref:System.Activities.Statements.ForEach%601> ve <xref:System.Activities.Statements.Assign%601> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="dc11b-104">In this sample, an activity is created at runtime with a body that contains a <xref:System.Activities.Statements.Sequence> activity that contains <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.Assign%601> activities.</span></span> <span data-ttu-id="dc11b-105">Bir giriş listesi tamsayıların etkinliğe geçilen ve bir özellik olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="dc11b-105">An input list of integers is passed into the activity and set as a property.</span></span> <span data-ttu-id="dc11b-106"><xref:System.Activities.Statements.ForEach%601> Etkinliği sonra değerler listesi üzerinde yinelenir ve bu öğelerden.</span><span class="sxs-lookup"><span data-stu-id="dc11b-106">The <xref:System.Activities.Statements.ForEach%601> activity then iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="dc11b-107">İçinde <xref:System.Activities.Statements.Assign%601> etkinlik, ortalama değer listesindeki öğelerin sayısı tarafından accumulator bölünmesiyle hesaplanır ve ortalama olarak atayın.</span><span class="sxs-lookup"><span data-stu-id="dc11b-107">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assign it to the average.</span></span>  
  
 <span data-ttu-id="dc11b-108">Örnek kullanımını gösteren bir <xref:System.Activities.DynamicActivity> giriş bağımsız değişkenleri ve değerler olarak döndüren olarak değişkenleri akar etkinlik çıkışı bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="dc11b-108">The sample demonstrates the usage of a <xref:System.Activities.DynamicActivity> activity that flows in variables as input arguments and returning values as output arguments.</span></span> <span data-ttu-id="dc11b-109">Etkinlik adlı bir giriş bağımsız değişkenine sahip `Numbers` tamsayı olan bir listesi.</span><span class="sxs-lookup"><span data-stu-id="dc11b-109">The activity has one input argument named `Numbers` that is a list of integers.</span></span> <span data-ttu-id="dc11b-110"><xref:System.Activities.Statements.ForEach%601> Etkinlik değerler listesi ilerler ve onu birikir.</span><span class="sxs-lookup"><span data-stu-id="dc11b-110">The <xref:System.Activities.Statements.ForEach%601> activity iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="dc11b-111">İçinde <xref:System.Activities.Statements.Assign%601> etkinlik, ortalama değer listesindeki öğelerin sayısı tarafından accumulator bölme ve ortalama olarak atayarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="dc11b-111">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assigning it to the average.</span></span> <span data-ttu-id="dc11b-112">Ortalama adlı bir çıktı bağımsız değişken olarak döndürülür `Average`.</span><span class="sxs-lookup"><span data-stu-id="dc11b-112">The average is returned as an output argument named `Average`.</span></span>  
  
 <span data-ttu-id="dc11b-113">Dinamik etkinlik programlı olarak oluşturulduğunda, giriş ve çıkış aşağıdaki kod örneğinde gösterildiği gibi bildirilir.</span><span class="sxs-lookup"><span data-stu-id="dc11b-113">When the dynamic activity is created programmatically, the input and output are declared as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="dc11b-114">Aşağıdaki kod örneğinde tam tanımını gösterir `DynamicActivity` listesindeki değerlerin ortalamasını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="dc11b-114">The following code example shows the complete definition of the `DynamicActivity` that computes the average of the values in a list.</span></span>  
  
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
  
 <span data-ttu-id="dc11b-115">XAML'de oluşturduğunuzda, giriş ve çıkış aşağıdaki örnekte gösterildiği gibi bildirilir.</span><span class="sxs-lookup"><span data-stu-id="dc11b-115">When created in XAML, the input and output are declared as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="dc11b-116">XAML görsel olarak kullanılarak oluşturulabilir [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dc11b-116">The XAML can be created visually using the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="dc11b-117">Visual Studio projesi içinde yer alıyorsa, "yapı derlenmiş gelen önlemek için Eylem" "None" ayarladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="dc11b-117">If it is included in a Visual Studio project, be sure to set its "Build Action" to "None" to prevent it from being compiled.</span></span> <span data-ttu-id="dc11b-118">XAML sonra aşağıdaki çağrıyı kullanarak dinamik olarak yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="dc11b-118">The XAML can then be loaded dynamically using the following call.</span></span>  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 <span data-ttu-id="dc11b-119"><xref:System.Activities.DynamicActivity> Örneği oluşturulan programlı olarak veya bir XAML yükleme aracılığıyla iş akışı aşağıdaki kod örneğinde gösterildiği gibi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc11b-119">The <xref:System.Activities.DynamicActivity> instance created programmatically or through loading a XAML workflow can be used as shown in the following code example.</span></span> <span data-ttu-id="dc11b-120">Lütfen "işlem" için unutmayın `WorkflowInvoker.Invoke` "işlemidir" <xref:System.Activities.Activity> ilk kod örneğinde tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="dc11b-120">Please note that "act" passed to the `WorkflowInvoker.Invoke` is the "act" <xref:System.Activities.Activity> defined in the first code example.</span></span>  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="dc11b-121">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="dc11b-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="dc11b-122">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], DynamicActivityCreation.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="dc11b-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DynamicActivityCreation.sln solution file.</span></span>  
  
2.  <span data-ttu-id="dc11b-123">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dc11b-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="dc11b-124">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dc11b-124">To run the solution, press CTRL+F5.</span></span>  
  
## <a name="command-line-arguments"></a><span data-ttu-id="dc11b-125">Komut satırı bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="dc11b-125">Command line arguments</span></span>  
 <span data-ttu-id="dc11b-126">Bu örnek komut satırı bağımsız değişkenlerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="dc11b-126">This sample accepts command line arguments.</span></span> <span data-ttu-id="dc11b-127">Kullanıcılar kendi ortalamayı hesaplamak için etkinliği sayıdan oluşan bir liste sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc11b-127">Users can provide a list of numbers for the activity to calculate their average.</span></span> <span data-ttu-id="dc11b-128">Kullanılacak sayı listesi boşlukla ayrılmış sayıdan oluşan bir liste olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="dc11b-128">The list of numbers to be used is passed as a list of numbers separated by a space.</span></span> <span data-ttu-id="dc11b-129">Örneğin, hesaplamak için 5, 10 ve 32 ortalaması çağırma aşağıdaki komut satırını kullanarak örneği.</span><span class="sxs-lookup"><span data-stu-id="dc11b-129">For example, to calculate the average of 5, 10, and 32 invoke the sample using the following command line.</span></span>  
  
 <span data-ttu-id="dc11b-130">**DynamicActivityCreation 5 10 32**</span><span class="sxs-lookup"><span data-stu-id="dc11b-130">**DynamicActivityCreation 5 10 32**</span></span>  
> [!IMPORTANT]
>  <span data-ttu-id="dc11b-131">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc11b-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dc11b-132">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="dc11b-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dc11b-133">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="dc11b-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dc11b-134">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="dc11b-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`  
  
## <a name="see-also"></a><span data-ttu-id="dc11b-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc11b-135">See Also</span></span>
