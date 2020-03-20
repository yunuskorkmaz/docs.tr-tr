---
title: Genel Olmayan ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 08dbac3974915f823a4f6e39f35927453a7c4b3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142712"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="b123a-102">Genel Olmayan ForEach</span><span class="sxs-lookup"><span data-stu-id="b123a-102">Non-Generic ForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="b123a-103">alet çantasında, koleksiyonlar aracılığıyla <xref:System.Activities.Statements.ForEach%601> <xref:System.Collections.Generic.IEnumerable%601> yineleme sağlayan, dahil olmak üzere bir dizi Kontrol Akışı aktivitesi gemi.</span><span class="sxs-lookup"><span data-stu-id="b123a-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>  
  
 <span data-ttu-id="b123a-104"><xref:System.Activities.Statements.ForEach%601>özelliğinin <xref:System.Activities.Statements.ForEach%601.Values%2A> türünün <xref:System.Collections.Generic.IEnumerable%601>olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b123a-104"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="b123a-105">Bu, kullanıcıların arabirimi uygulayan <xref:System.Collections.Generic.IEnumerable%601> veri yapıları üzerinde yinelemelerini <xref:System.Collections.ArrayList>(örneğin,) engellemez.</span><span class="sxs-lookup"><span data-stu-id="b123a-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="b123a-106">Genel olmayan sürümü, <xref:System.Activities.Statements.ForEach%601> koleksiyondaki değer türlerinin uyumluluğunu sağlamak için daha fazla çalışma süresi karmaşıklığı pahasına bu gereksinimin üstesinden gelir.</span><span class="sxs-lookup"><span data-stu-id="b123a-106">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="b123a-107">Bu örnek, genel <xref:System.Activities.Statements.ForEach%601> olmayan bir etkinliğin ve tasarımcısının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b123a-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="b123a-108">Bu etkinlik, <xref:System.Collections.ArrayList>'' ile yinelemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b123a-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="b123a-109">Foreach Etkinliği</span><span class="sxs-lookup"><span data-stu-id="b123a-109">ForEach Activity</span></span>  
 <span data-ttu-id="b123a-110">C#/Visual Basic `foreach` deyimi, koleksiyonun her öğesi için katışılmış bir deyim çalıştırarak koleksiyonun öğelerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="b123a-110">The C#/Visual Basic `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="b123a-111">Eşdeğer [!INCLUDE[wf1](../../../../includes/wf1-md.md)] faaliyetleri `foreach` ve <xref:System.Activities.Statements.ForEach%601> <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="b123a-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="b123a-112">Etkinlik, <xref:System.Activities.Statements.ForEach%601> değerlerin ve gövdenin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b123a-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="b123a-113">Çalışma zamanında, liste yinelenir ve gövde listedeki her değer için yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b123a-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="b123a-114">Çoğu durumda, kullanılacağı senaryoların çoğunu kapsadığından ve derleme zamanında tür denetimi sağladığından, etkinliğin genel sürümü tercih edilen çözüm olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b123a-114">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="b123a-115">Genel olmayan sürüm, genel <xref:System.Collections.IEnumerable> olmayan arabirimi uygulayan türleri yineleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b123a-115">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="b123a-116">Sınıf Tanımı</span><span class="sxs-lookup"><span data-stu-id="b123a-116">Class Definition</span></span>  
 <span data-ttu-id="b123a-117">Aşağıdaki kod örneği, genel `ForEach` olmayan bir etkinliğin tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b123a-117">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
```csharp  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }
}  
```  
  
 <span data-ttu-id="b123a-118">Gövde (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="b123a-118">Body (optional)</span></span>  
 <span data-ttu-id="b123a-119"><xref:System.Activities.ActivityAction> Koleksiyondaki <xref:System.Object>her öğe için yürütülen tür.</span><span class="sxs-lookup"><span data-stu-id="b123a-119">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="b123a-120">Her bir element kendi `Argument` özelliği aracılığıyla Vücuda geçirilir.</span><span class="sxs-lookup"><span data-stu-id="b123a-120">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="b123a-121">Değerler (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="b123a-121">Values (optional)</span></span>  
 <span data-ttu-id="b123a-122">Üzerinde yinelenir öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b123a-122">The collection of elements that are iterated over.</span></span> <span data-ttu-id="b123a-123">Koleksiyonun tüm öğelerinin uyumlu türlerde olmasını sağlamak çalışma zamanında yapılır.</span><span class="sxs-lookup"><span data-stu-id="b123a-123">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="b123a-124">ForEach Kullanma Örneği</span><span class="sxs-lookup"><span data-stu-id="b123a-124">Example of Using ForEach</span></span>  
 <span data-ttu-id="b123a-125">Aşağıdaki kod, bir uygulamada ForEach etkinliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b123a-125">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
```csharp  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
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
  
|<span data-ttu-id="b123a-126">Koşul</span><span class="sxs-lookup"><span data-stu-id="b123a-126">Condition</span></span>|<span data-ttu-id="b123a-127">İleti</span><span class="sxs-lookup"><span data-stu-id="b123a-127">Message</span></span>|<span data-ttu-id="b123a-128">Severity</span><span class="sxs-lookup"><span data-stu-id="b123a-128">Severity</span></span>|<span data-ttu-id="b123a-129">Özel Durum Türü</span><span class="sxs-lookup"><span data-stu-id="b123a-129">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="b123a-130">Değerler,`null`</span><span class="sxs-lookup"><span data-stu-id="b123a-130">Values is `null`</span></span>|<span data-ttu-id="b123a-131">Gerekli bir etkinlik bağımsız değişkeni 'Değerler' için değer sağlanmadı.</span><span class="sxs-lookup"><span data-stu-id="b123a-131">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="b123a-132">Hata</span><span class="sxs-lookup"><span data-stu-id="b123a-132">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="b123a-133">Foreach Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="b123a-133">ForEach Designer</span></span>  
 <span data-ttu-id="b123a-134">Örnek için etkinlik tasarımcısı, yerleşik <xref:System.Activities.Statements.ForEach%601> etkinlik için sağlanan tasarımcıya görünüm olarak benzerdir.</span><span class="sxs-lookup"><span data-stu-id="b123a-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="b123a-135">Tasarımcı, **Örnekler**, **Genel Olmayan Etkinlikler** kategorisinde ki araç kutusunda görünür.</span><span class="sxs-lookup"><span data-stu-id="b123a-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="b123a-136">Etkinlik, düzgün yapılandırılmış bir aktivite oluşturur araç kutusunda bir <xref:System.Activities.Presentation.IActivityTemplateFactory> ortaya çıkarır, çünkü tasarımcı, araç kutusunda **ForEachWithBodyFactory** <xref:System.Activities.ActivityAction>adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b123a-136">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```csharp  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
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
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="b123a-137">Bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b123a-137">To run this sample</span></span>  
  
1. <span data-ttu-id="b123a-138">Seçtiğiniz projeyi çözümün başlangıç projesi olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="b123a-138">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1. <span data-ttu-id="b123a-139">**CodeTestClient,** kodu kullanarak etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b123a-139">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2. <span data-ttu-id="b123a-140">**DesignerTestClient,** tasarımcı içindeki etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b123a-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2. <span data-ttu-id="b123a-141">Projeyi oluşturun ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b123a-141">Build and run the project.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b123a-142">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="b123a-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b123a-143">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b123a-143">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b123a-144">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="b123a-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b123a-145">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="b123a-145">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
