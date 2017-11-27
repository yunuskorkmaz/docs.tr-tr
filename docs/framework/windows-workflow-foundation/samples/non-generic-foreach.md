---
title: Genel olmayan ForEach
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 234e5a7ef9591c1e943484402bc235b62ad7fb87
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="non-generic-foreach"></a><span data-ttu-id="44ad2-102">Genel olmayan ForEach</span><span class="sxs-lookup"><span data-stu-id="44ad2-102">Non-Generic ForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="44ad2-103">kendi araç kutusunda etkinlikleri, akış denetimi dahil olmak üzere bir dizi gelir <xref:System.Activities.Statements.ForEach%601>, böylece üzerinden yineleme <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` koleksiyonları.</span><span class="sxs-lookup"><span data-stu-id="44ad2-103"> ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` collections.</span></span>  
  
 <span data-ttu-id="44ad2-104"><xref:System.Activities.Statements.ForEach%601>gerektirir, <xref:System.Activities.Statements.ForEach%601.Values%2A> türünde olması özelliği <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="44ad2-104"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`.</span></span> <span data-ttu-id="44ad2-105">Bu uygulama veri yapıları yineleme kullanıcılar önleyen <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` arabirimi (örneğin, <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="44ad2-105">This precludes users from iterating over data structures that implement <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="44ad2-106">Genel olmayan sürümü <xref:System.Activities.Statements.ForEach%601> koleksiyondaki değerlerin türleri uyumluluğu sağlamaya yönelik daha fazla çalışma zamanı karmaşıklık ödün verme pahasına bu gereksinimi ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="44ad2-106">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="44ad2-107">Bu örnek, genel olmayan uygulamak gösterilmiştir <xref:System.Activities.Statements.ForEach%601> etkinliği ve onun Tasarımcısı.</span><span class="sxs-lookup"><span data-stu-id="44ad2-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="44ad2-108">Bu etkinlik yinelemek için kullanılabilecek <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="44ad2-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="44ad2-109">ForEach etkinliği</span><span class="sxs-lookup"><span data-stu-id="44ad2-109">ForEach Activity</span></span>  
 <span data-ttu-id="44ad2-110">C# /VB `foreach` deyimi koleksiyonunun her öğe için katıştırılmış bir deyimi yürütme bir koleksiyonun öğelerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="44ad2-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="44ad2-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Eşdeğer etkinliklerini `foreach` olan <xref:System.Activities.Statements.ForEach%601> ve <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="44ad2-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="44ad2-112"><xref:System.Activities.Statements.ForEach%601> Etkinlik değerleri ve gövde listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="44ad2-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="44ad2-113">Çalışma zamanında listesi yinelendiğinde ve listedeki her bir değer için gövdesi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="44ad2-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="44ad2-114">Kullanılacak ve tür derleme zamanında denetlemesini sağlar senaryoları çoğunu kapsar çünkü çoğu durumda, tercih edilen bir çözüm etkinlik genel sürümü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="44ad2-114">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="44ad2-115">Genel olmayan uygulama türleri aracılığıyla yineleme için genel olmayan sürüm kullanılabilir <xref:System.Collections.IEnumerable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="44ad2-115">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="44ad2-116">Sınıf tanımı</span><span class="sxs-lookup"><span data-stu-id="44ad2-116">Class Definition</span></span>  
 <span data-ttu-id="44ad2-117">Aşağıdaki kod örneğinde genel olmayan tanımını gösterir `ForEach` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="44ad2-117">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
```  
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
  
 <span data-ttu-id="44ad2-118">Gövde (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="44ad2-118">Body (optional)</span></span>  
 <span data-ttu-id="44ad2-119"><xref:System.Activities.ActivityAction> Türü <xref:System.Object>, koleksiyondaki her öğe için yürütüldü.</span><span class="sxs-lookup"><span data-stu-id="44ad2-119">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="44ad2-120">Her öğesi gövdesine geçirilen kendi `Argument` özelliği.</span><span class="sxs-lookup"><span data-stu-id="44ad2-120">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="44ad2-121">Değerleri (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="44ad2-121">Values (optional)</span></span>  
 <span data-ttu-id="44ad2-122">Üzerinden yinelendiğinde öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="44ad2-122">The collection of elements that are iterated over.</span></span> <span data-ttu-id="44ad2-123">Tüm koleksiyon öğelerini uyumlu türleri emin olma çalışma zamanında yapılır.</span><span class="sxs-lookup"><span data-stu-id="44ad2-123">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="44ad2-124">ForEach kullanma örneği</span><span class="sxs-lookup"><span data-stu-id="44ad2-124">Example of Using ForEach</span></span>  
 <span data-ttu-id="44ad2-125">Aşağıdaki kod bir uygulamada ForEach etkinlik kullanımı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="44ad2-125">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
```  
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
  
|<span data-ttu-id="44ad2-126">Koşul</span><span class="sxs-lookup"><span data-stu-id="44ad2-126">Condition</span></span>|<span data-ttu-id="44ad2-127">İleti</span><span class="sxs-lookup"><span data-stu-id="44ad2-127">Message</span></span>|<span data-ttu-id="44ad2-128">Önem Derecesi</span><span class="sxs-lookup"><span data-stu-id="44ad2-128">Severity</span></span>|<span data-ttu-id="44ad2-129">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="44ad2-129">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="44ad2-130">Değerler`null`</span><span class="sxs-lookup"><span data-stu-id="44ad2-130">Values is `null`</span></span>|<span data-ttu-id="44ad2-131">Gerekli etkinlik bağımsız değişkeni 'Değerleri' için değer girilmedi.</span><span class="sxs-lookup"><span data-stu-id="44ad2-131">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="44ad2-132">Hata</span><span class="sxs-lookup"><span data-stu-id="44ad2-132">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="44ad2-133">ForEach Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="44ad2-133">ForEach Designer</span></span>  
 <span data-ttu-id="44ad2-134">Örnek etkinlik Tasarımcısı için yerleşik sağlanan Tasarımcısı görünümüne benzer <xref:System.Activities.Statements.ForEach%601> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="44ad2-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="44ad2-135">Araç kutusunda Tasarımcı görünür **örnekleri**, **olmayan genel etkinlikleri** kategorisi.</span><span class="sxs-lookup"><span data-stu-id="44ad2-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="44ad2-136">Tasarımcı adlı **ForEachWithBodyFactory** araç kutusunda etkinlik sunan çünkü bir <xref:System.Activities.Presentation.IActivityTemplateFactory> araç kutusunda oluşturan etkinliğin bir düzgün yapılandırılmış <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="44ad2-136">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```  
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
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="44ad2-137">Bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="44ad2-137">To run this sample</span></span>  
  
1.  <span data-ttu-id="44ad2-138">Projenin tercih ettiğiniz çözüm başlangıç projesi olarak ayarla:</span><span class="sxs-lookup"><span data-stu-id="44ad2-138">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1.  <span data-ttu-id="44ad2-139">**CodeTestClient** kodu kullanarak etkinliğini kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="44ad2-139">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2.  <span data-ttu-id="44ad2-140">**DesignerTestClient** etkinlik Tasarımcısı'nda kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="44ad2-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2.  <span data-ttu-id="44ad2-141">Oluşturun ve projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="44ad2-141">Build and run the project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="44ad2-142">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="44ad2-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="44ad2-143">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="44ad2-143">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="44ad2-144">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="44ad2-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="44ad2-145">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="44ad2-145">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
