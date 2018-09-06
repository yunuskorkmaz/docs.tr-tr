---
title: Genel olmayan ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 70d5de587dda3cb61205a8d77f2173df9b93498b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881817"
---
# <a name="non-generic-parallelforeach"></a><span data-ttu-id="3d47d-102">Genel olmayan ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="3d47d-102">Non-Generic ParallelForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="3d47d-103"> kendi araç kutusunda etkinlikler, akış denetimi dahil olmak üzere bir dizi birlikte gelen <xref:System.Activities.Statements.ParallelForEach%601>, üzerinden yineleme olanak tanıyan <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` koleksiyonları.</span><span class="sxs-lookup"><span data-stu-id="3d47d-103"> ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ParallelForEach%601>, which allows iterating through <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` collections.</span></span>  
  
 <span data-ttu-id="3d47d-104"><xref:System.Activities.Statements.ParallelForEach%601> gerektirir, <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> türünde olmasını özelliği <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="3d47d-104"><xref:System.Activities.Statements.ParallelForEach%601> requires its <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> property to be of type <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`.</span></span> <span data-ttu-id="3d47d-105">Bu kullanıcılar, uygulama veri yapıları üzerinde yineleme gelen ışığının <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` arabirimi (örneğin, <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="3d47d-105">This precludes users from iterating over data structures that implement <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="3d47d-106">Genel olmayan sürümü <xref:System.Activities.Statements.ParallelForEach%601> koleksiyonundaki değerleri türlerinin uyumluluğu sağlamaya yönelik daha fazla çalışma zamanı karmaşıklığı çoğaltamaz bu gereksinimi ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3d47d-106">The non-generic version of <xref:System.Activities.Statements.ParallelForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="3d47d-107">Bu örnek, genel olmayan bir uygulama gösterilmektedir <xref:System.Activities.Statements.ParallelForEach%601> etkinlik ve iş Tasarımcısı.</span><span class="sxs-lookup"><span data-stu-id="3d47d-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ParallelForEach%601> activity and its designer.</span></span> <span data-ttu-id="3d47d-108">Bu etkinlik yinelemek için kullanılabilir <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="3d47d-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="parallelforeach-activity"></a><span data-ttu-id="3d47d-109">ParallelForEach etkinliği</span><span class="sxs-lookup"><span data-stu-id="3d47d-109">ParallelForEach Activity</span></span>  
 <span data-ttu-id="3d47d-110">C# /VB `foreach` deyimi koleksiyonundaki her öğe için bir katıştırılmış deyim yürütülürken, bir koleksiyonun öğeleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="3d47d-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="3d47d-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Eşdeğer etkinlikler <xref:System.Activities.Statements.ForEach%601> ve <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="3d47d-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="3d47d-112"><xref:System.Activities.Statements.ForEach%601> Etkinlik değerleri ve gövde listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="3d47d-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="3d47d-113">Çalışma zamanında, listenin yinelenir ve listedeki her değerin gövdesi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="3d47d-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="3d47d-114"><xref:System.Activities.Statements.ParallelForEach%601> sahip bir <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, böylece <xref:System.Activities.Statements.ParallelForEach%601> etkinliği tamamlamak erken varsa değerlendirmesi <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="3d47d-114"><xref:System.Activities.Statements.ParallelForEach%601> has a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, so that the <xref:System.Activities.Statements.ParallelForEach%601> activity could complete early if the evaluation of the <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> returns `true`.</span></span> <span data-ttu-id="3d47d-115"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Her yineleme tamamlandıktan sonra değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3d47d-115">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> is evaluated after each iteration is completed.</span></span>  
  
 <span data-ttu-id="3d47d-116">Burada kullanılır ve derleme zamanında tür sağlar senaryoları çoğunu kapsar için çoğu durumda, tercih edilen bir çözüm etkinliğin genel sürüm olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d47d-116">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it is used and provides type checking at compile time.</span></span> <span data-ttu-id="3d47d-117">Genel olmayan sürümü, genel olmayan uygulayan türler yineleme için kullanılabilir <xref:System.Collections.IEnumerable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3d47d-117">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="3d47d-118">Sınıf tanımı</span><span class="sxs-lookup"><span data-stu-id="3d47d-118">Class Definition</span></span>  
 <span data-ttu-id="3d47d-119">Aşağıdaki kod örneği, genel olmayan bir tanımı gösterilmektedir `ParallelForEach` etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="3d47d-119">The following code example shows the definition of a non-generic `ParallelForEach` activity is.</span></span>  
  
```  
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
  
 <span data-ttu-id="3d47d-120">Gövde (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="3d47d-120">Body (optional)</span></span>  
 <span data-ttu-id="3d47d-121"><xref:System.Activities.ActivityAction> Türü <xref:System.Object>, koleksiyondaki her öğe için gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3d47d-121">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="3d47d-122">Her bağımsız öğede gövdesine, bağımsız değişken özelliği üzerinden geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3d47d-122">Each individual element is passed into the Body through its Argument property.</span></span>  
  
 <span data-ttu-id="3d47d-123">Değer (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="3d47d-123">Values (optional)</span></span>  
 <span data-ttu-id="3d47d-124">Üzerinden yinelenir öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3d47d-124">The collection of elements that are iterated over.</span></span> <span data-ttu-id="3d47d-125">Tüm koleksiyon öğelerini uyumlu bir tür olduğundan emin olmak için çalışma zamanında gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3d47d-125">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
 <span data-ttu-id="3d47d-126">CompletionCondition (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="3d47d-126">CompletionCondition (optional)</span></span>  
 <span data-ttu-id="3d47d-127"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Özelliği, tüm yineleme tamamlandıktan sonra değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3d47d-127">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> property is evaluated after any iteration completes.</span></span> <span data-ttu-id="3d47d-128">Değerlendirilirse `true`, sonra zamanlanan yinelemeler iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="3d47d-128">If it evaluates to `true`, then the scheduled pending iterations are canceled.</span></span> <span data-ttu-id="3d47d-129">Bu özellik ayarlanmamışsa, dallar koleksiyondaki tüm etkinlikleri işlem tamamlanana kadar yürütün.</span><span class="sxs-lookup"><span data-stu-id="3d47d-129">If this property is not set, all activities in the Branches collection execute until completion.</span></span>  
  
## <a name="example-of-using-parallelforeach"></a><span data-ttu-id="3d47d-130">ParallelForEach kullanma örneği</span><span class="sxs-lookup"><span data-stu-id="3d47d-130">Example of Using ParallelForEach</span></span>  
 <span data-ttu-id="3d47d-131">Aşağıdaki kod bir uygulamada ParallelForEach etkinlik kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d47d-131">The following code demonstrates how to use the ParallelForEach activity in an application.</span></span>  
  
```  
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
  
## <a name="parallelforeach-designer"></a><span data-ttu-id="3d47d-132">ParallelForEach Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="3d47d-132">ParallelForEach Designer</span></span>  
 <span data-ttu-id="3d47d-133">Örnek etkinlik Tasarımcısı için yerleşik sağlanan Tasarımcı görünümü benzer <xref:System.Activities.Statements.ParallelForEach%601> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="3d47d-133">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span> <span data-ttu-id="3d47d-134">Tasarımcı araç kutusunda görünür **örnekleri**, **genel olmayan etkinlikler** kategorisi.</span><span class="sxs-lookup"><span data-stu-id="3d47d-134">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="3d47d-135">Tasarımcı adlı **ParallelForEachWithBodyFactory** Araç Kutusu'nda, etkinlik kullanıma sunduğundan bir <xref:System.Activities.Presentation.IActivityTemplateFactory> etkinliği bir düzgün bir şekilde yapılandırılmış oluşturan araç kutusunda <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="3d47d-135">The designer is named **ParallelForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox that creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```  
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
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="3d47d-136">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3d47d-136">To run the sample</span></span>  
  
1.  <span data-ttu-id="3d47d-137">Seçtiğiniz proje, çözümün başlangıç projesi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3d47d-137">Set the project of your choice as the startup project of the solution.</span></span>  
  
    1.  <span data-ttu-id="3d47d-138">**CodeTestClient** kod kullanarak etkinliğini kullanma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d47d-138">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2.  <span data-ttu-id="3d47d-139">**DesignerTestClient** etkinlik Tasarımcısı içinde kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d47d-139">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2.  <span data-ttu-id="3d47d-140">Derleme ve projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3d47d-140">Build and run the project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3d47d-141">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="3d47d-141">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3d47d-142">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3d47d-142">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3d47d-143">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="3d47d-143">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3d47d-144">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3d47d-144">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
