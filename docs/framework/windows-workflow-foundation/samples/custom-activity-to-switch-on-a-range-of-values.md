---
title: "Özel Etkinlik bir aralık değerleri anahtara"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ff6a55157e886b54d631d1ca5d2598785de7608d
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a><span data-ttu-id="91a7b-102">Özel Etkinlik bir aralık değerleri anahtara</span><span class="sxs-lookup"><span data-stu-id="91a7b-102">Custom Activity to Switch on a Range of Values</span></span>
<span data-ttu-id="91a7b-103">Bu örnek kullanımını genişleten bir özel etkinlik oluşturmak nasıl gösteren bir <xref:System.Activities.Statements.Switch%601>.</span><span class="sxs-lookup"><span data-stu-id="91a7b-103">This sample demonstrates how to create a custom activity that extends the use of a <xref:System.Activities.Statements.Switch%601>.</span></span> <span data-ttu-id="91a7b-104">Geleneksel <xref:System.Activities.Statements.Switch%601> deyimi sağlar geçiş dayalı tek bir değer.</span><span class="sxs-lookup"><span data-stu-id="91a7b-104">A conventional <xref:System.Activities.Statements.Switch%601> statement allows switching based upon a single value.</span></span> <span data-ttu-id="91a7b-105">Ancak, bir etkinlik burada geçmelidir senaryolarını değerleri aralığı alarak iş vardır.</span><span class="sxs-lookup"><span data-stu-id="91a7b-105">But, there are business scenarios where an activity must switch based upon a range of values.</span></span> <span data-ttu-id="91a7b-106">Örneğin, bir etkinlik bağlı anahtarlı değeri 1 ile 5 arasında olduğunda bir eylem, değer 6 ile 10 arasında olduğunda başka bir eylem ve diğer tüm değerler için varsayılan eylem yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="91a7b-106">For example, an activity might execute one action when the value being switched upon is between 1 and 5, another action when the value is between 6 and 10, and a default action for all other values.</span></span> <span data-ttu-id="91a7b-107">Bu özel etkinlik tam olarak bu senaryo sağlar.</span><span class="sxs-lookup"><span data-stu-id="91a7b-107">This custom activity enables exactly that scenario.</span></span>  
  
## <a name="the-switchrange-activity"></a><span data-ttu-id="91a7b-108">SwitchRange etkinliği</span><span class="sxs-lookup"><span data-stu-id="91a7b-108">The SwitchRange Activity</span></span>  
 <span data-ttu-id="91a7b-109">`SwitchRange` Etkinlik zamanlar alt etkinlik, ifadesinin sonucu değer bir aralık içinde dahil edildiğinde, `Cases`.</span><span class="sxs-lookup"><span data-stu-id="91a7b-109">The `SwitchRange` activity schedules a child activity when the result value of its expression is included within the range of one of its `Cases`.</span></span>  
  
 <span data-ttu-id="91a7b-110">Aşağıdaki kod örneğinde anahtarları değerleri aralığı dayalı özel bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="91a7b-110">The following code example is a custom activity that switches based upon a range of values.</span></span>  
  
```csharp  
public sealed class SwitchRange<T> : NativeActivity where T : IComparable  
{  
   [RequiredArgument]  
   [DefaultValue(null)]  
   public InArgument<T> Expression { get; set; }  
  
   public IList<CaseRange<T>> Cases  
  
   [DefaultValue(null)]  
   public Activity Default { get; set; }}  
}  
```  
  
|<span data-ttu-id="91a7b-111">Özellik</span><span class="sxs-lookup"><span data-stu-id="91a7b-111">Property</span></span>|<span data-ttu-id="91a7b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91a7b-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="91a7b-113">İfade</span><span class="sxs-lookup"><span data-stu-id="91a7b-113">Expression</span></span>|<span data-ttu-id="91a7b-114">Bu hesaplanan ve durumları listesinde aralıkları karşı karşılaştırıldığında ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="91a7b-114">This is the expression to be evaluated and compared against the ranges in the Cases list.</span></span> <span data-ttu-id="91a7b-115">T türünde ifade sonucu</span><span class="sxs-lookup"><span data-stu-id="91a7b-115">The result of the expression is of type T.</span></span>|  
|<span data-ttu-id="91a7b-116">Durumları</span><span class="sxs-lookup"><span data-stu-id="91a7b-116">Cases</span></span>|<span data-ttu-id="91a7b-117">Her durumda, bir aralığı (başlangıç ve bitiş) ve bir etkinlik (gövde) oluşur.</span><span class="sxs-lookup"><span data-stu-id="91a7b-117">Each case consists of a range (From and To) and an activity (Body).</span></span> <span data-ttu-id="91a7b-118">İfade değerlendirilir ve karşı aralıkları karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="91a7b-118">The expression is evaluated and compared against the ranges.</span></span> <span data-ttu-id="91a7b-119">İfadenin sonucu örneklerinin bir aralık içinde ise, karşılık gelen etkinlik yürütülür.</span><span class="sxs-lookup"><span data-stu-id="91a7b-119">If the result of the expression is within the range of one of the cases, the corresponding activity is executed.</span></span>|  
|<span data-ttu-id="91a7b-120">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="91a7b-120">Default</span></span>|<span data-ttu-id="91a7b-121">Hiçbir durumda eşleştiğinde çalıştırılan etkinliği.</span><span class="sxs-lookup"><span data-stu-id="91a7b-121">The activity that is executed when no case is matched.</span></span> <span data-ttu-id="91a7b-122">Ayarlandığında `null`, hiçbir işlem yapılmadı.</span><span class="sxs-lookup"><span data-stu-id="91a7b-122">When set to `null`, no action is taken.</span></span>|  
  
## <a name="caserange-class"></a><span data-ttu-id="91a7b-123">CaseRange sınıfı</span><span class="sxs-lookup"><span data-stu-id="91a7b-123">CaseRange Class</span></span>  
 <span data-ttu-id="91a7b-124">`CaseRange` Sınıfı temsil eden bir aralıkta bir `SwitchRange` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="91a7b-124">The `CaseRange` class represents a range within a `SwitchRange` activity.</span></span> <span data-ttu-id="91a7b-125">Her örneğinin `CaseRange` bir aralık içerdiği (oluşan bir `From` ve `To`) ve bir `Body` , zamanlanan etkinlik ifade `SwitchRange` aralık içinde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="91a7b-125">Every instance of `CaseRange` contains a range (composed of a `From` and a `To`) and a `Body` activity that is scheduled if the expression in the `SwitchRange` is evaluated within the range.</span></span>  
  
 <span data-ttu-id="91a7b-126">Aşağıdaki kod örneği için tanım `CaseRange` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="91a7b-126">The following code example is the definition for the `CaseRange` class.</span></span>  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="91a7b-127">Hem `SwitchRange` ve `CaseRange` örnekte tanımlanan sınıflar sınıflardır uygulayan herhangi bir türü ile çalışabilirsiniz genel `IComparable`gibi <xref:System.Activities.Statements.Switch%601> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="91a7b-127">Both the `SwitchRange` and `CaseRange` classes, which are defined in the sample are generic classes that can work with any type that implements `IComparable`, like the <xref:System.Activities.Statements.Switch%601> class.</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="91a7b-128">Örnek Kullanım</span><span class="sxs-lookup"><span data-stu-id="91a7b-128">Sample Usage</span></span>  
 <span data-ttu-id="91a7b-129">Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya `SwitchRange` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="91a7b-129">The following code example demonstrates how to use the `SwitchRange` activity.</span></span>  
  
```csharp  
Activity SwitchRange = new SwitchRange<int>  
{  
    Expression = new InArgument<int>(value),  
    Cases =   
    {  
        new CaseRange<int>                      
        {  
            From = 1,  
            To = 5,  
            Action = new WriteLine  
            {  
                Text = "Case 1-5 selected",  
            }  
        },  
        new CaseRange<int>  
        {  
            From = 6,  
            To = 10,  
            Action = new WriteLine  
            {  
                Text = "Case 6-10 selected",  
            }  
        }  
    },  
    Default = new WriteLine { Text = "Default Case selected" }  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="91a7b-130">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="91a7b-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="91a7b-131">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], SwitchRange.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="91a7b-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the SwitchRange.sln solution file.</span></span>  
  
2.  <span data-ttu-id="91a7b-132">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91a7b-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="91a7b-133">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91a7b-133">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="91a7b-134">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="91a7b-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="91a7b-135">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="91a7b-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="91a7b-136">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="91a7b-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="91a7b-137">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="91a7b-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`