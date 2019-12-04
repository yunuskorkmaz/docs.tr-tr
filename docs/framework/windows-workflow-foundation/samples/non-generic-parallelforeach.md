---
title: Genel olmayan ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 33e0c8ef8c04b7d58815760ae1152f63891fdfd5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715638"
---
# <a name="non-generic-parallelforeach"></a><span data-ttu-id="d138c-102">Genel olmayan ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="d138c-102">Non-generic ParallelForEach</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="d138c-103">, <xref:System.Collections.Generic.IEnumerable%601> koleksiyonları arasında yineleme sağlayan <xref:System.Activities.Statements.ParallelForEach%601>de dahil olmak üzere bir denetim akışı etkinliği kümesi araç kutusuna gönderilir.</span><span class="sxs-lookup"><span data-stu-id="d138c-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ParallelForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>

<span data-ttu-id="d138c-104"><xref:System.Activities.Statements.ParallelForEach%601>, <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> özelliğinin <xref:System.Collections.Generic.IEnumerable%601>türünde olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d138c-104"><xref:System.Activities.Statements.ParallelForEach%601> requires its <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> property to be of type  <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="d138c-105">Bu, kullanıcıların <xref:System.Collections.Generic.IEnumerable%601> arabirimi (örneğin, <xref:System.Collections.ArrayList>) uygulayan veri yapıları üzerinde yinelenmesine neden olacak.</span><span class="sxs-lookup"><span data-stu-id="d138c-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="d138c-106"><xref:System.Activities.Statements.ParallelForEach%601> genel olmayan sürümü bu gereksinimi, koleksiyondaki değer türlerinin uyumluluğunu sağlamaya yönelik daha fazla çalışma zamanı karmaşıklığı masrafına göre daha fazla gelir.</span><span class="sxs-lookup"><span data-stu-id="d138c-106">The non-generic version of <xref:System.Activities.Statements.ParallelForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>

<span data-ttu-id="d138c-107">Bu örnek, genel olmayan <xref:System.Activities.Statements.ParallelForEach%601> etkinliğinin ve tasarımcısının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d138c-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ParallelForEach%601> activity and its designer.</span></span> <span data-ttu-id="d138c-108">Bu etkinlik <xref:System.Collections.ArrayList>üzerinden yinelemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d138c-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>

## <a name="parallelforeach-activity"></a><span data-ttu-id="d138c-109">ParallelForEach etkinliği</span><span class="sxs-lookup"><span data-stu-id="d138c-109">ParallelForEach activity</span></span>

<span data-ttu-id="d138c-110">C#/Vb `foreach` ifade, bir koleksiyonun öğelerini numaralandırır ve koleksiyonun her öğesi için gömülü bir ifade yürütüyordur.</span><span class="sxs-lookup"><span data-stu-id="d138c-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="d138c-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] denk etkinlikler <xref:System.Activities.Statements.ForEach%601> ve <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="d138c-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="d138c-112"><xref:System.Activities.Statements.ForEach%601> etkinliği bir değer ve gövde listesi içerir.</span><span class="sxs-lookup"><span data-stu-id="d138c-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="d138c-113">Çalışma zamanında, liste tekrarlandırılır ve listedeki her bir değer için gövde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d138c-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>

<span data-ttu-id="d138c-114"><xref:System.Activities.Statements.ParallelForEach%601>, <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> değerlendirmesi `true`döndürürse <xref:System.Activities.Statements.ParallelForEach%601> etkinliğinin erken tamamlanabilmesi için bir <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>vardır.</span><span class="sxs-lookup"><span data-stu-id="d138c-114"><xref:System.Activities.Statements.ParallelForEach%601> has a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, so that the <xref:System.Activities.Statements.ParallelForEach%601> activity could complete early if the evaluation of the <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> returns `true`.</span></span> <span data-ttu-id="d138c-115"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> her yineleme tamamlandıktan sonra değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d138c-115">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> is evaluated after each iteration is completed.</span></span>

<span data-ttu-id="d138c-116">Çoğu durumda, etkinliğin genel sürümü tercih edilen çözüm olmalıdır, çünkü kullanıldığı senaryoların çoğunu kapsamakta ve derleme zamanında tür denetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d138c-116">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it is used and provides type checking at compile time.</span></span> <span data-ttu-id="d138c-117">Genel olmayan sürüm, genel olmayan <xref:System.Collections.IEnumerable> arabirimini uygulayan türler arasında yineleme yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d138c-117">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>

## <a name="class-definition"></a><span data-ttu-id="d138c-118">Sınıf tanımı</span><span class="sxs-lookup"><span data-stu-id="d138c-118">Class definition</span></span>

<span data-ttu-id="d138c-119">Aşağıdaki kod örneği, genel olmayan `ParallelForEach` etkinliğinin tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d138c-119">The following code example shows the definition of a non-generic `ParallelForEach` activity is.</span></span>

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

<span data-ttu-id="d138c-120">Gövde (isteğe bağlı) </span><span class="sxs-lookup"><span data-stu-id="d138c-120">Body (optional)</span></span>\
<span data-ttu-id="d138c-121">Koleksiyondaki her öğe için yürütülen <xref:System.Object>türü <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="d138c-121">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="d138c-122">Bağımsız değişken özelliği aracılığıyla her bir öğe gövdeye iletilir.</span><span class="sxs-lookup"><span data-stu-id="d138c-122">Each individual element is passed into the Body through its Argument property.</span></span>

<span data-ttu-id="d138c-123">Değerler (isteğe bağlı) </span><span class="sxs-lookup"><span data-stu-id="d138c-123">Values (optional)</span></span>\
<span data-ttu-id="d138c-124">Tekrarlandırılmış öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d138c-124">The collection of elements that are iterated over.</span></span> <span data-ttu-id="d138c-125">Koleksiyondaki tüm öğelerin uyumlu türlerde olduğundan emin olmak, çalışma zamanında yapılır.</span><span class="sxs-lookup"><span data-stu-id="d138c-125">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>

<span data-ttu-id="d138c-126">CompletionCondition (isteğe bağlı) </span><span class="sxs-lookup"><span data-stu-id="d138c-126">CompletionCondition (optional)</span></span>\
<span data-ttu-id="d138c-127"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> özelliği herhangi bir yineleme tamamlandıktan sonra değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d138c-127">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> property is evaluated after any iteration completes.</span></span> <span data-ttu-id="d138c-128">`true`değerlendirilirse, zamanlanan bekleyen yinelemeler iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="d138c-128">If it evaluates to `true`, then the scheduled pending iterations are canceled.</span></span> <span data-ttu-id="d138c-129">Bu özellik ayarlanmamışsa, dallar koleksiyonundaki tüm etkinlikler tamamlanana kadar yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d138c-129">If this property is not set, all activities in the Branches collection execute until completion.</span></span>

## <a name="example-of-using-parallelforeach"></a><span data-ttu-id="d138c-130">ParallelForEach kullanma örneği</span><span class="sxs-lookup"><span data-stu-id="d138c-130">Example of using ParallelForEach</span></span>

<span data-ttu-id="d138c-131">Aşağıdaki kod, bir uygulamada ParallelForEach etkinliğinin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d138c-131">The following code demonstrates how to use the ParallelForEach activity in an application.</span></span>

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

## <a name="parallelforeach-designer"></a><span data-ttu-id="d138c-132">ParallelForEach Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="d138c-132">ParallelForEach designer</span></span>

<span data-ttu-id="d138c-133">Örnek için etkinlik Tasarımcısı, yerleşik <xref:System.Activities.Statements.ParallelForEach%601> etkinliği için sunulan tasarımcı görünümünde benzerdir.</span><span class="sxs-lookup"><span data-stu-id="d138c-133">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span> <span data-ttu-id="d138c-134">Tasarımcı, **örnekler**, **genel olmayan etkinlikler** kategorisindeki araç kutusunda görünür.</span><span class="sxs-lookup"><span data-stu-id="d138c-134">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="d138c-135">Tasarımcı araç kutusunda **ParallelForEachWithBodyFactory** olarak adlandırılır, çünkü etkinlik, uygun şekilde yapılandırılmış bir <xref:System.Activities.ActivityAction>etkinlik oluşturan araç kutusunda bir <xref:System.Activities.Presentation.IActivityTemplateFactory> kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="d138c-135">The designer is named **ParallelForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox that creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>

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

## <a name="to-run-the-sample"></a><span data-ttu-id="d138c-136">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d138c-136">To run the sample</span></span>

1. <span data-ttu-id="d138c-137">Tercih ettiğiniz projeyi çözümün başlangıç projesi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d138c-137">Set the project of your choice as the startup project of the solution.</span></span>

    1. <span data-ttu-id="d138c-138">**Codetekstclient** , kodu kullanarak etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d138c-138">**CodeTestClient** shows how to use the activity using code.</span></span>

    2. <span data-ttu-id="d138c-139">**DesignerTestClient** , etkinliğin tasarımcı içinde nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d138c-139">**DesignerTestClient** shows how to use the activity within the designer.</span></span>

2. <span data-ttu-id="d138c-140">Projeyi derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d138c-140">Build and run the project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d138c-141">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d138c-141">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d138c-142">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d138c-142">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d138c-143">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="d138c-143">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d138c-144">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d138c-144">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
