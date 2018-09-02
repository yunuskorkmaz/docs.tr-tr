---
title: DynamicActivity oluşturma
ms.date: 03/30/2017
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
ms.openlocfilehash: 270066fafd5c71b2a720ca305433159c172872aa
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385267"
---
# <a name="dynamicactivity-creation"></a><span data-ttu-id="596c9-102">DynamicActivity oluşturma</span><span class="sxs-lookup"><span data-stu-id="596c9-102">DynamicActivity Creation</span></span>
<span data-ttu-id="596c9-103">Bu örnek, çalışma zamanı kullanarak bir etkinlik oluşturmak için iki farklı yol gösterir. <xref:System.Activities.DynamicActivity> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="596c9-103">This sample demonstrates two different ways to create an activity at runtime using the <xref:System.Activities.DynamicActivity> activity.</span></span>  
  
 <span data-ttu-id="596c9-104">Bu örnekte, bir etkinlik içeren bir gövde ile çalışma zamanında oluşturulan bir <xref:System.Activities.Statements.Sequence> içeren etkinlik <xref:System.Activities.Statements.ForEach%601> ve <xref:System.Activities.Statements.Assign%601> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="596c9-104">In this sample, an activity is created at runtime with a body that contains a <xref:System.Activities.Statements.Sequence> activity that contains <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.Assign%601> activities.</span></span> <span data-ttu-id="596c9-105">Giriş bir tamsayı listesi etkinliğini geçirilen ve bir özellik olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="596c9-105">An input list of integers is passed into the activity and set as a property.</span></span> <span data-ttu-id="596c9-106"><xref:System.Activities.Statements.ForEach%601> Etkinliği ardından değerleri listesi yinelenir ve onu toplanır.</span><span class="sxs-lookup"><span data-stu-id="596c9-106">The <xref:System.Activities.Statements.ForEach%601> activity then iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="596c9-107">İçinde <xref:System.Activities.Statements.Assign%601> etkinlik, ortalama değer listesindeki öğelerin sayısını accumulator bölünerek hesaplanır ve ortalama olarak atayın.</span><span class="sxs-lookup"><span data-stu-id="596c9-107">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assign it to the average.</span></span>  
  
 <span data-ttu-id="596c9-108">Örnek, kullanımını gösterir. bir <xref:System.Activities.DynamicActivity> çıktı bağımsız değişkenlerinde giriş bağımsız değişkenleri ve değerler olarak döndüren olarak akış etkinliği.</span><span class="sxs-lookup"><span data-stu-id="596c9-108">The sample demonstrates the usage of a <xref:System.Activities.DynamicActivity> activity that flows in variables as input arguments and returning values as output arguments.</span></span> <span data-ttu-id="596c9-109">Adlı bir giriş bağımsız değişkeni etkinliğinde `Numbers` tamsayı olan bir listesi.</span><span class="sxs-lookup"><span data-stu-id="596c9-109">The activity has one input argument named `Numbers` that is a list of integers.</span></span> <span data-ttu-id="596c9-110"><xref:System.Activities.Statements.ForEach%601> Etkinliği değerleri listesi yinelenir ve onu toplanır.</span><span class="sxs-lookup"><span data-stu-id="596c9-110">The <xref:System.Activities.Statements.ForEach%601> activity iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="596c9-111">İçinde <xref:System.Activities.Statements.Assign%601> accumulator listedeki öğelerin sayısına göre bölme ve ortalama olarak atayarak etkinlik, ortalama değer hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="596c9-111">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assigning it to the average.</span></span> <span data-ttu-id="596c9-112">Ortalama adlı çıktı bağımsız değişken olarak döndürülen `Average`.</span><span class="sxs-lookup"><span data-stu-id="596c9-112">The average is returned as an output argument named `Average`.</span></span>  
  
 <span data-ttu-id="596c9-113">Zvolit dynamickou programlı bir şekilde oluşturulduğunda, giriş ve çıkış aşağıdaki kod örneğinde gösterildiği gibi bildirilir.</span><span class="sxs-lookup"><span data-stu-id="596c9-113">When the dynamic activity is created programmatically, the input and output are declared as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="596c9-114">Aşağıdaki kod örneği eksiksiz tanımını gösterir `DynamicActivity` , listedeki değerlerin ortalamasını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="596c9-114">The following code example shows the complete definition of the `DynamicActivity` that computes the average of the values in a list.</span></span>  
  
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
  
 <span data-ttu-id="596c9-115">XAML içinde oluştururken, giriş ve çıkış aşağıdaki örnekte gösterildiği gibi bildirilir.</span><span class="sxs-lookup"><span data-stu-id="596c9-115">When created in XAML, the input and output are declared as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="596c9-116">XAML görsel olarak kullanılarak oluşturulabilir. [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="596c9-116">The XAML can be created visually using the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="596c9-117">Visual Studio projesi içinde yer alıyorsa "Derleme Eylemi'ni önlemek için Eylem" için "None" ayarladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="596c9-117">If it is included in a Visual Studio project, be sure to set its "Build Action" to "None" to prevent it from being compiled.</span></span> <span data-ttu-id="596c9-118">XAML, ardından aşağıdaki çağrı kullanılarak dinamik olarak yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="596c9-118">The XAML can then be loaded dynamically using the following call.</span></span>  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 <span data-ttu-id="596c9-119"><xref:System.Activities.DynamicActivity> Örneği oluşturulan programlı olarak veya bir XAML yüklenirken aracılığıyla iş akışı aşağıdaki kod örneğinde gösterildiği gibi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="596c9-119">The <xref:System.Activities.DynamicActivity> instance created programmatically or through loading a XAML workflow can be used as shown in the following code example.</span></span> <span data-ttu-id="596c9-120">"İşlem" geçirilen olduğunu lütfen unutmayın `WorkflowInvoker.Invoke` "işlemidir" <xref:System.Activities.Activity> ilk kod örneğinde tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="596c9-120">Please note that "act" passed to the `WorkflowInvoker.Invoke` is the "act" <xref:System.Activities.Activity> defined in the first code example.</span></span>  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="596c9-121">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="596c9-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="596c9-122">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], DynamicActivityCreation.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="596c9-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DynamicActivityCreation.sln solution file.</span></span>  
  
2.  <span data-ttu-id="596c9-123">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="596c9-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="596c9-124">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="596c9-124">To run the solution, press CTRL+F5.</span></span>  
  
## <a name="command-line-arguments"></a><span data-ttu-id="596c9-125">Komut satırı bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="596c9-125">Command line arguments</span></span>  
 <span data-ttu-id="596c9-126">Bu örnek, komut satırı bağımsız değişkenlerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="596c9-126">This sample accepts command line arguments.</span></span> <span data-ttu-id="596c9-127">Kullanıcılar kendi ortalamayı hesaplamak için etkinliğin sayıdan oluşan bir liste sağlar.</span><span class="sxs-lookup"><span data-stu-id="596c9-127">Users can provide a list of numbers for the activity to calculate their average.</span></span> <span data-ttu-id="596c9-128">Kullanılacak sayı listesi boşlukla ayırarak sayıdan oluşan bir liste olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="596c9-128">The list of numbers to be used is passed as a list of numbers separated by a space.</span></span> <span data-ttu-id="596c9-129">Örneğin, hesaplamak için ortalama 5, 10 ve 32 çağırma şu komut satırını kullanarak örneği.</span><span class="sxs-lookup"><span data-stu-id="596c9-129">For example, to calculate the average of 5, 10, and 32 invoke the sample using the following command line.</span></span>  
  
 <span data-ttu-id="596c9-130">**DynamicActivityCreation 5 10 32**</span><span class="sxs-lookup"><span data-stu-id="596c9-130">**DynamicActivityCreation 5 10 32**</span></span>  
> [!IMPORTANT]
>  <span data-ttu-id="596c9-131">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="596c9-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="596c9-132">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="596c9-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="596c9-133">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="596c9-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="596c9-134">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="596c9-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`