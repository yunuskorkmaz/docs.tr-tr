---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: genel olmayan ParallelForEach'
title: Genel olmayan ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 9eaa4ed565fa00a0479f21d907fe5433317d88f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741945"
---
# <a name="non-generic-parallelforeach"></a><span data-ttu-id="7fa97-103">Genel olmayan ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="7fa97-103">Non-generic ParallelForEach</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="7fa97-104">, kendi araç kutusunda, <xref:System.Activities.Statements.ParallelForEach%601> koleksiyonlar arasında yineleme sağlayan denetim akışı etkinlikleri kümesi olarak gelir <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="7fa97-104">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ParallelForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>

<span data-ttu-id="7fa97-105"><xref:System.Activities.Statements.ParallelForEach%601><xref:System.Activities.Statements.ParallelForEach%601.Values%2A>özelliğinin türünde olması gerekir <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="7fa97-105"><xref:System.Activities.Statements.ParallelForEach%601> requires its <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> property to be of type  <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="7fa97-106">Bu <xref:System.Collections.Generic.IEnumerable%601> , kullanıcıların arabirimi (örneğin,) uygulayan veri yapıları üzerinde yinelenmesine neden olacak <xref:System.Collections.ArrayList> .</span><span class="sxs-lookup"><span data-stu-id="7fa97-106">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="7fa97-107">Genel olmayan sürüm, <xref:System.Activities.Statements.ParallelForEach%601> koleksiyondaki değer türlerinin uyumluluğunu sağlamaya yönelik daha fazla çalışma zamanı karmaşıklığı masrafına bu gereksinimi verir.</span><span class="sxs-lookup"><span data-stu-id="7fa97-107">The non-generic version of <xref:System.Activities.Statements.ParallelForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>

<span data-ttu-id="7fa97-108">Bu örnek, genel olmayan bir <xref:System.Activities.Statements.ParallelForEach%601> etkinliğin ve tasarımcısının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fa97-108">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ParallelForEach%601> activity and its designer.</span></span> <span data-ttu-id="7fa97-109">Bu etkinlik, üzerinden yinelemek için kullanılabilir <xref:System.Collections.ArrayList> .</span><span class="sxs-lookup"><span data-stu-id="7fa97-109">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>

## <a name="parallelforeach-activity"></a><span data-ttu-id="7fa97-110">ParallelForEach etkinliği</span><span class="sxs-lookup"><span data-stu-id="7fa97-110">ParallelForEach activity</span></span>

<span data-ttu-id="7fa97-111">C#/Visual Basic `foreach` ifade bir koleksiyonun öğelerini numaralandırır ve koleksiyonun her öğesi için gömülü bir ifade yürütüyordur.</span><span class="sxs-lookup"><span data-stu-id="7fa97-111">The C#/Visual Basic `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="7fa97-112">[!INCLUDE[wf1](../../../../includes/wf1-md.md)]Eşdeğer etkinlikler <xref:System.Activities.Statements.ForEach%601> ve ' dir <xref:System.Activities.Statements.ParallelForEach%601> .</span><span class="sxs-lookup"><span data-stu-id="7fa97-112">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="7fa97-113"><xref:System.Activities.Statements.ForEach%601>Etkinlik bir değer ve gövde listesi içerir.</span><span class="sxs-lookup"><span data-stu-id="7fa97-113">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="7fa97-114">Çalışma zamanında, liste tekrarlandırılır ve listedeki her bir değer için gövde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="7fa97-114">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>

<span data-ttu-id="7fa97-115"><xref:System.Activities.Statements.ParallelForEach%601> , ' a sahip olduğundan <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> , <xref:System.Activities.Statements.ParallelForEach%601> geri dönüşler değerlendirmesi durumunda etkinliğin erken tamamlanabilmesi için <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> `true` .</span><span class="sxs-lookup"><span data-stu-id="7fa97-115"><xref:System.Activities.Statements.ParallelForEach%601> has a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, so that the <xref:System.Activities.Statements.ParallelForEach%601> activity could complete early if the evaluation of the <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> returns `true`.</span></span> <span data-ttu-id="7fa97-116"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>Her yineleme tamamlandıktan sonra değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="7fa97-116">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> is evaluated after each iteration is completed.</span></span>

<span data-ttu-id="7fa97-117">Çoğu durumda, etkinliğin genel sürümü tercih edilen çözüm olmalıdır, çünkü kullanıldığı senaryoların çoğunu kapsamakta ve derleme zamanında tür denetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7fa97-117">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it is used and provides type checking at compile time.</span></span> <span data-ttu-id="7fa97-118">Genel olmayan sürüm, genel olmayan arabirimi uygulayan türler arasında yineleme yapmak için kullanılabilir <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="7fa97-118">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>

## <a name="class-definition"></a><span data-ttu-id="7fa97-119">Sınıf tanımı</span><span class="sxs-lookup"><span data-stu-id="7fa97-119">Class definition</span></span>

<span data-ttu-id="7fa97-120">Aşağıdaki kod örneği, genel olmayan bir etkinliğin tanımını gösterir `ParallelForEach` .</span><span class="sxs-lookup"><span data-stu-id="7fa97-120">The following code example shows the definition of a non-generic `ParallelForEach` activity is.</span></span>

```csharp
[ContentProperty("Body")]
public class ParallelForEach : NativeActivity
{
    [RequiredArgument]
    [DefaultValue(null)]
    InArgument<IEnumerable> Values { get; set; }

    [DefaultValue(null)]
    [DependsOn("Values")]
    public Activity<bool> CompletionCondition
    [DefaultValue(null)]
    [DependsOn("CompletionCondition")]
    ActivityAction<object> Body { get; set; }
}
```

<span data-ttu-id="7fa97-121">Gövde (isteğe bağlı) </span><span class="sxs-lookup"><span data-stu-id="7fa97-121">Body (optional)</span></span>\
<span data-ttu-id="7fa97-122"><xref:System.Activities.ActivityAction> <xref:System.Object> Koleksiyondaki her öğe için yürütülen türü.</span><span class="sxs-lookup"><span data-stu-id="7fa97-122">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="7fa97-123">Bağımsız değişken özelliği aracılığıyla her bir öğe gövdeye iletilir.</span><span class="sxs-lookup"><span data-stu-id="7fa97-123">Each individual element is passed into the Body through its Argument property.</span></span>

<span data-ttu-id="7fa97-124">Değerler (isteğe bağlı) </span><span class="sxs-lookup"><span data-stu-id="7fa97-124">Values (optional)</span></span>\
<span data-ttu-id="7fa97-125">Tekrarlandırılmış öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7fa97-125">The collection of elements that are iterated over.</span></span> <span data-ttu-id="7fa97-126">Koleksiyondaki tüm öğelerin uyumlu türlerde olduğundan emin olmak, çalışma zamanında yapılır.</span><span class="sxs-lookup"><span data-stu-id="7fa97-126">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>

<span data-ttu-id="7fa97-127">CompletionCondition (isteğe bağlı) </span><span class="sxs-lookup"><span data-stu-id="7fa97-127">CompletionCondition (optional)</span></span>\
<span data-ttu-id="7fa97-128"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>Özellik, herhangi bir yineleme tamamlandıktan sonra değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="7fa97-128">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> property is evaluated after any iteration completes.</span></span> <span data-ttu-id="7fa97-129">Olarak değerlendirilirse `true` , zamanlanan bekleyen yinelemeler iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="7fa97-129">If it evaluates to `true`, then the scheduled pending iterations are canceled.</span></span> <span data-ttu-id="7fa97-130">Bu özellik ayarlanmamışsa, dallar koleksiyonundaki tüm etkinlikler tamamlanana kadar yürütülür.</span><span class="sxs-lookup"><span data-stu-id="7fa97-130">If this property is not set, all activities in the Branches collection execute until completion.</span></span>

## <a name="example-of-using-parallelforeach"></a><span data-ttu-id="7fa97-131">ParallelForEach kullanma örneği</span><span class="sxs-lookup"><span data-stu-id="7fa97-131">Example of using ParallelForEach</span></span>

<span data-ttu-id="7fa97-132">Aşağıdaki kod, bir uygulamada ParallelForEach etkinliğinin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7fa97-132">The following code demonstrates how to use the ParallelForEach activity in an application.</span></span>

```csharp
string[] names = { "bill", "steve", "ray" };

DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };

Activity sampleUsage =
    new ParallelForEach
    {
       Values = new InArgument<IEnumerable>(c=> names),
       Body = new ActivityAction<object>
       {
           Argument = iterationVariable,
           Handler = new WriteLine
           {
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))
           }
       }
   };
```

## <a name="parallelforeach-designer"></a><span data-ttu-id="7fa97-133">ParallelForEach Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="7fa97-133">ParallelForEach designer</span></span>

<span data-ttu-id="7fa97-134">Örnek için etkinlik Tasarımcısı, yerleşik etkinlik için sunulan tasarımcı görünümünde benzerdir <xref:System.Activities.Statements.ParallelForEach%601> .</span><span class="sxs-lookup"><span data-stu-id="7fa97-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span> <span data-ttu-id="7fa97-135">Tasarımcı, **örnekler**, **genel olmayan etkinlikler** kategorisindeki araç kutusunda görünür.</span><span class="sxs-lookup"><span data-stu-id="7fa97-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="7fa97-136">Tasarımcı araç kutusunda **ParallelForEachWithBodyFactory** olarak adlandırılır, çünkü etkinlik, <xref:System.Activities.Presentation.IActivityTemplateFactory> düzgün bir şekilde yapılandırılmış olan etkinliği oluşturan araç kutusunda bir araç gösterir <xref:System.Activities.ActivityAction> .</span><span class="sxs-lookup"><span data-stu-id="7fa97-136">The designer is named **ParallelForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox that creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>

```csharp
public sealed class ParallelForEachWithBodyFactory : IActivityTemplateFactory
{
    public Activity Create(DependencyObject target)
    {
        return new Microsoft.Samples.Activities.Statements.ParallelForEach()
        {
            Body = new ActivityAction<object>()
            {
                Argument = new DelegateInArgument<object>()
                {
                    Name = "item"
                }
            }
        };
    }
}
```

## <a name="to-run-the-sample"></a><span data-ttu-id="7fa97-137">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7fa97-137">To run the sample</span></span>

1. <span data-ttu-id="7fa97-138">Tercih ettiğiniz projeyi çözümün başlangıç projesi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7fa97-138">Set the project of your choice as the startup project of the solution.</span></span>

    1. <span data-ttu-id="7fa97-139">**Codetekstclient** , kodu kullanarak etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fa97-139">**CodeTestClient** shows how to use the activity using code.</span></span>

    2. <span data-ttu-id="7fa97-140">**DesignerTestClient** , etkinliğin tasarımcı içinde nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fa97-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>

2. <span data-ttu-id="7fa97-141">Projeyi derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7fa97-141">Build and run the project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7fa97-142">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7fa97-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7fa97-143">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7fa97-143">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7fa97-144">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7fa97-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7fa97-145">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7fa97-145">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
