---
title: Genel Olmayan ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: cb040d8bd5fbb34cc00b246f2e51789866fd8e78
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989033"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="f5344-102">Genel Olmayan ForEach</span><span class="sxs-lookup"><span data-stu-id="f5344-102">Non-Generic ForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="f5344-103">, kendi araç kutusunda, <xref:System.Activities.Statements.ForEach%601>koleksiyonlar arasında <xref:System.Collections.Generic.IEnumerable%601> yineleme sağlayan denetim akışı etkinlikleri kümesi olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="f5344-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>  
  
 <span data-ttu-id="f5344-104"><xref:System.Activities.Statements.ForEach%601><xref:System.Activities.Statements.ForEach%601.Values%2A> özelliğinin türünde<xref:System.Collections.Generic.IEnumerable%601>olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5344-104"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="f5344-105">Bu, kullanıcıların arabirimi (örneğin, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.ArrayList>) uygulayan veri yapıları üzerinde yinelenmesine neden olacak.</span><span class="sxs-lookup"><span data-stu-id="f5344-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="f5344-106">Genel olmayan sürüm <xref:System.Activities.Statements.ForEach%601> , koleksiyondaki değer türlerinin uyumluluğunu sağlamaya yönelik daha fazla çalışma zamanı karmaşıklığı masrafına bu gereksinimi verir.</span><span class="sxs-lookup"><span data-stu-id="f5344-106">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="f5344-107">Bu örnek, genel <xref:System.Activities.Statements.ForEach%601> olmayan bir etkinliğin ve tasarımcısının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5344-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="f5344-108">Bu etkinlik, üzerinden <xref:System.Collections.ArrayList>yinelemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5344-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="f5344-109">ForEach etkinliği</span><span class="sxs-lookup"><span data-stu-id="f5344-109">ForEach Activity</span></span>  
 <span data-ttu-id="f5344-110">C#/Vb `foreach` ekstresi bir koleksiyonun öğelerini numaralandırır ve koleksiyonun her öğesi için gömülü bir ifade yürütüyordur.</span><span class="sxs-lookup"><span data-stu-id="f5344-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="f5344-111">Eşdeğer etkinlikleri ve <xref:System.Activities.Statements.ForEach%601> ' dir<xref:System.Activities.Statements.ParallelForEach%601>. `foreach` [!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5344-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="f5344-112"><xref:System.Activities.Statements.ForEach%601> Etkinlik bir değer ve gövde listesi içerir.</span><span class="sxs-lookup"><span data-stu-id="f5344-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="f5344-113">Çalışma zamanında, liste tekrarlandırılır ve listedeki her bir değer için gövde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="f5344-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="f5344-114">Çoğu durumda, etkinliğin genel sürümünün tercih edilen çözüm olması gerekir, çünkü bu, kullanılacağı senaryoların çoğunu kapsamakta ve derleme zamanında tür denetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5344-114">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="f5344-115">Genel olmayan sürüm, genel <xref:System.Collections.IEnumerable> olmayan arabirimi uygulayan türler arasında yineleme yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5344-115">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="f5344-116">Sınıf tanımı</span><span class="sxs-lookup"><span data-stu-id="f5344-116">Class Definition</span></span>  
 <span data-ttu-id="f5344-117">Aşağıdaki kod örneği genel `ForEach` olmayan bir etkinliğin tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5344-117">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
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
  
 <span data-ttu-id="f5344-118">Gövde (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="f5344-118">Body (optional)</span></span>  
 <span data-ttu-id="f5344-119">Koleksiyondaki her öğe için yürütülen türü <xref:System.Object>. <xref:System.Activities.ActivityAction></span><span class="sxs-lookup"><span data-stu-id="f5344-119">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="f5344-120">Her tek öğe, `Argument` özelliği aracılığıyla gövdeye geçirilir.</span><span class="sxs-lookup"><span data-stu-id="f5344-120">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="f5344-121">Değerler (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="f5344-121">Values (optional)</span></span>  
 <span data-ttu-id="f5344-122">Tekrarlandırılmış öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f5344-122">The collection of elements that are iterated over.</span></span> <span data-ttu-id="f5344-123">Koleksiyondaki tüm öğelerin uyumlu türlerde olduğundan emin olmak, çalışma zamanında yapılır.</span><span class="sxs-lookup"><span data-stu-id="f5344-123">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="f5344-124">ForEach kullanma örneği</span><span class="sxs-lookup"><span data-stu-id="f5344-124">Example of Using ForEach</span></span>  
 <span data-ttu-id="f5344-125">Aşağıdaki kod, bir uygulamada ForEach etkinliğinin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f5344-125">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
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
  
|<span data-ttu-id="f5344-126">Koşul</span><span class="sxs-lookup"><span data-stu-id="f5344-126">Condition</span></span>|<span data-ttu-id="f5344-127">`Message`</span><span class="sxs-lookup"><span data-stu-id="f5344-127">Message</span></span>|<span data-ttu-id="f5344-128">Önem Derecesi</span><span class="sxs-lookup"><span data-stu-id="f5344-128">Severity</span></span>|<span data-ttu-id="f5344-129">Özel Durum Türü</span><span class="sxs-lookup"><span data-stu-id="f5344-129">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="f5344-130">Değerler`null`</span><span class="sxs-lookup"><span data-stu-id="f5344-130">Values is `null`</span></span>|<span data-ttu-id="f5344-131">Gerekli etkinlik bağımsız değişkeni ' Values ' değeri sağlanmadı.</span><span class="sxs-lookup"><span data-stu-id="f5344-131">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="f5344-132">Hata</span><span class="sxs-lookup"><span data-stu-id="f5344-132">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="f5344-133">ForEach Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="f5344-133">ForEach Designer</span></span>  
 <span data-ttu-id="f5344-134">Örnek için etkinlik Tasarımcısı, yerleşik <xref:System.Activities.Statements.ForEach%601> etkinlik için sunulan tasarımcı görünümünde benzerdir.</span><span class="sxs-lookup"><span data-stu-id="f5344-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="f5344-135">Tasarımcı, **örnekler**, **genel olmayan etkinlikler** kategorisindeki araç kutusunda görünür.</span><span class="sxs-lookup"><span data-stu-id="f5344-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="f5344-136">Tasarımcı araç kutusunda **ForEachWithBodyFactory** olarak adlandırılır çünkü etkinlik <xref:System.Activities.Presentation.IActivityTemplateFactory> , düzgün bir şekilde yapılandırılmış <xref:System.Activities.ActivityAction>olan etkinliği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f5344-136">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
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
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="f5344-137">Bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f5344-137">To run this sample</span></span>  
  
1. <span data-ttu-id="f5344-138">Tercih ettiğiniz projeyi çözümün başlangıç projesi olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="f5344-138">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1. <span data-ttu-id="f5344-139">**Codetekstclient** , kodu kullanarak etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5344-139">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2. <span data-ttu-id="f5344-140">**DesignerTestClient** , etkinliğin tasarımcı içinde nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5344-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2. <span data-ttu-id="f5344-141">Derleme ve projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f5344-141">Build and run the project.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f5344-142">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5344-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f5344-143">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f5344-143">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f5344-144">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="f5344-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f5344-145">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f5344-145">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
