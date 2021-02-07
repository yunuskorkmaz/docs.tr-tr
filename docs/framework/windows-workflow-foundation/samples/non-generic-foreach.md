---
description: 'Hakkında daha fazla bilgi edinin: genel olmayan ForEach'
title: Genel Olmayan ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 16635da4ef57ff7b59e178f5954465d8b86bf488
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741958"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="0513b-103">Genel Olmayan ForEach</span><span class="sxs-lookup"><span data-stu-id="0513b-103">Non-Generic ForEach</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="0513b-104">, kendi araç kutusunda, <xref:System.Activities.Statements.ForEach%601> koleksiyonlar arasında yineleme sağlayan denetim akışı etkinlikleri kümesi olarak gelir <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="0513b-104">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>  
  
 <span data-ttu-id="0513b-105"><xref:System.Activities.Statements.ForEach%601><xref:System.Activities.Statements.ForEach%601.Values%2A>özelliğinin türünde olması gerekir <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="0513b-105"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="0513b-106">Bu <xref:System.Collections.Generic.IEnumerable%601> , kullanıcıların arabirimi (örneğin,) uygulayan veri yapıları üzerinde yinelenmesine neden olacak <xref:System.Collections.ArrayList> .</span><span class="sxs-lookup"><span data-stu-id="0513b-106">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="0513b-107">Genel olmayan sürüm, <xref:System.Activities.Statements.ForEach%601> koleksiyondaki değer türlerinin uyumluluğunu sağlamaya yönelik daha fazla çalışma zamanı karmaşıklığı masrafına bu gereksinimi verir.</span><span class="sxs-lookup"><span data-stu-id="0513b-107">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="0513b-108">Bu örnek, genel olmayan bir <xref:System.Activities.Statements.ForEach%601> etkinliğin ve tasarımcısının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0513b-108">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="0513b-109">Bu etkinlik, üzerinden yinelemek için kullanılabilir <xref:System.Collections.ArrayList> .</span><span class="sxs-lookup"><span data-stu-id="0513b-109">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="0513b-110">ForEach etkinliği</span><span class="sxs-lookup"><span data-stu-id="0513b-110">ForEach Activity</span></span>  

 <span data-ttu-id="0513b-111">C#/Visual Basic `foreach` ifade bir koleksiyonun öğelerini numaralandırır ve koleksiyonun her öğesi için gömülü bir ifade yürütüyordur.</span><span class="sxs-lookup"><span data-stu-id="0513b-111">The C#/Visual Basic `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="0513b-112">[!INCLUDE[wf1](../../../../includes/wf1-md.md)]Eşdeğer etkinlikleri `foreach` <xref:System.Activities.Statements.ForEach%601> ve ' dir <xref:System.Activities.Statements.ParallelForEach%601> .</span><span class="sxs-lookup"><span data-stu-id="0513b-112">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="0513b-113"><xref:System.Activities.Statements.ForEach%601>Etkinlik bir değer ve gövde listesi içerir.</span><span class="sxs-lookup"><span data-stu-id="0513b-113">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="0513b-114">Çalışma zamanında, liste tekrarlandırılır ve listedeki her bir değer için gövde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="0513b-114">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="0513b-115">Çoğu durumda, etkinliğin genel sürümünün tercih edilen çözüm olması gerekir, çünkü bu, kullanılacağı senaryoların çoğunu kapsamakta ve derleme zamanında tür denetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0513b-115">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="0513b-116">Genel olmayan sürüm, genel olmayan arabirimi uygulayan türler arasında yineleme yapmak için kullanılabilir <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="0513b-116">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="0513b-117">Sınıf tanımı</span><span class="sxs-lookup"><span data-stu-id="0513b-117">Class Definition</span></span>  

 <span data-ttu-id="0513b-118">Aşağıdaki kod örneği genel olmayan bir etkinliğin tanımını gösterir `ForEach` .</span><span class="sxs-lookup"><span data-stu-id="0513b-118">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
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
  
 <span data-ttu-id="0513b-119">Gövde (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="0513b-119">Body (optional)</span></span>  
 <span data-ttu-id="0513b-120"><xref:System.Activities.ActivityAction> <xref:System.Object> Koleksiyondaki her öğe için yürütülen türü.</span><span class="sxs-lookup"><span data-stu-id="0513b-120">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="0513b-121">Her tek öğe, özelliği aracılığıyla gövdeye geçirilir `Argument` .</span><span class="sxs-lookup"><span data-stu-id="0513b-121">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="0513b-122">Değerler (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="0513b-122">Values (optional)</span></span>  
 <span data-ttu-id="0513b-123">Tekrarlandırılmış öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0513b-123">The collection of elements that are iterated over.</span></span> <span data-ttu-id="0513b-124">Koleksiyondaki tüm öğelerin uyumlu türlerde olduğundan emin olmak, çalışma zamanında yapılır.</span><span class="sxs-lookup"><span data-stu-id="0513b-124">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="0513b-125">ForEach kullanma örneği</span><span class="sxs-lookup"><span data-stu-id="0513b-125">Example of Using ForEach</span></span>  

 <span data-ttu-id="0513b-126">Aşağıdaki kod, bir uygulamada ForEach etkinliğinin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="0513b-126">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
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
  
|<span data-ttu-id="0513b-127">Koşul</span><span class="sxs-lookup"><span data-stu-id="0513b-127">Condition</span></span>|<span data-ttu-id="0513b-128">İleti</span><span class="sxs-lookup"><span data-stu-id="0513b-128">Message</span></span>|<span data-ttu-id="0513b-129">Önem derecesi</span><span class="sxs-lookup"><span data-stu-id="0513b-129">Severity</span></span>|<span data-ttu-id="0513b-130">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="0513b-130">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="0513b-131">Değerler `null`</span><span class="sxs-lookup"><span data-stu-id="0513b-131">Values is `null`</span></span>|<span data-ttu-id="0513b-132">Gerekli etkinlik bağımsız değişkeni ' Values ' değeri sağlanmadı.</span><span class="sxs-lookup"><span data-stu-id="0513b-132">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="0513b-133">Hata</span><span class="sxs-lookup"><span data-stu-id="0513b-133">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="0513b-134">ForEach Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="0513b-134">ForEach Designer</span></span>  

 <span data-ttu-id="0513b-135">Örnek için etkinlik Tasarımcısı, yerleşik etkinlik için sunulan tasarımcı görünümünde benzerdir <xref:System.Activities.Statements.ForEach%601> .</span><span class="sxs-lookup"><span data-stu-id="0513b-135">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="0513b-136">Tasarımcı, **örnekler**, **genel olmayan etkinlikler** kategorisindeki araç kutusunda görünür.</span><span class="sxs-lookup"><span data-stu-id="0513b-136">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="0513b-137">Tasarımcı araç kutusunda **ForEachWithBodyFactory** olarak adlandırılır çünkü etkinlik, düzgün bir şekilde <xref:System.Activities.Presentation.IActivityTemplateFactory> yapılandırılmış olan etkinliği oluşturur <xref:System.Activities.ActivityAction> .</span><span class="sxs-lookup"><span data-stu-id="0513b-137">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
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
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="0513b-138">Bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0513b-138">To run this sample</span></span>  
  
1. <span data-ttu-id="0513b-139">Tercih ettiğiniz projeyi çözümün başlangıç projesi olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0513b-139">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1. <span data-ttu-id="0513b-140">**Codetekstclient** , kodu kullanarak etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0513b-140">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2. <span data-ttu-id="0513b-141">**DesignerTestClient** , etkinliğin tasarımcı içinde nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0513b-141">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2. <span data-ttu-id="0513b-142">Projeyi derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0513b-142">Build and run the project.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0513b-143">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="0513b-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0513b-144">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0513b-144">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0513b-145">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0513b-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0513b-146">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0513b-146">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
