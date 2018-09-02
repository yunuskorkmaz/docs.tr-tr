---
title: Üzerinde bir değer aralığına geçmek için özel etkinlik
ms.date: 03/30/2017
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
ms.openlocfilehash: cfaf4318b1557a9fc217de8254e164243ea54569
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417983"
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a><span data-ttu-id="44ff9-102">Üzerinde bir değer aralığına geçmek için özel etkinlik</span><span class="sxs-lookup"><span data-stu-id="44ff9-102">Custom Activity to Switch on a Range of Values</span></span>
<span data-ttu-id="44ff9-103">Bu örnek, kullanımını genişleten özel etkinlik oluşturma işlemini gösterir. bir <xref:System.Activities.Statements.Switch%601>.</span><span class="sxs-lookup"><span data-stu-id="44ff9-103">This sample demonstrates how to create a custom activity that extends the use of a <xref:System.Activities.Statements.Switch%601>.</span></span> <span data-ttu-id="44ff9-104">Geleneksel <xref:System.Activities.Statements.Switch%601> deyimi geçişi sırasında tek bir değer temel sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ff9-104">A conventional <xref:System.Activities.Statements.Switch%601> statement allows switching based upon a single value.</span></span> <span data-ttu-id="44ff9-105">Ancak, bir etkinlik burada geçmelidir senaryolarını değer aralığını alarak iş vardır.</span><span class="sxs-lookup"><span data-stu-id="44ff9-105">But, there are business scenarios where an activity must switch based upon a range of values.</span></span> <span data-ttu-id="44ff9-106">Örneğin, bir etkinlik, geçiş sırasında değeri 1 ile 5 arasında olduğunda bir eylem, değer 6 ile 10 arasında olduğunda başka bir eylem ve diğer tüm değerler için bir varsayılan eylem paralellikle çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="44ff9-106">For example, an activity might execute one action when the value being switched upon is between 1 and 5, another action when the value is between 6 and 10, and a default action for all other values.</span></span> <span data-ttu-id="44ff9-107">Bu özel etkinlik tam olarak bir senaryo sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ff9-107">This custom activity enables exactly that scenario.</span></span>  
  
## <a name="the-switchrange-activity"></a><span data-ttu-id="44ff9-108">SwitchRange etkinliği</span><span class="sxs-lookup"><span data-stu-id="44ff9-108">The SwitchRange Activity</span></span>  
 <span data-ttu-id="44ff9-109">`SwitchRange` Etkinliği, birinin aralığında, ifadenin sonucu değerini eklendiğinde bir alt etkinlik zamanlar kendi `Cases`.</span><span class="sxs-lookup"><span data-stu-id="44ff9-109">The `SwitchRange` activity schedules a child activity when the result value of its expression is included within the range of one of its `Cases`.</span></span>  
  
 <span data-ttu-id="44ff9-110">Aşağıdaki kod örneği, anahtarları değerleri aralığı alan özel bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="44ff9-110">The following code example is a custom activity that switches based upon a range of values.</span></span>  
  
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
  
|<span data-ttu-id="44ff9-111">Özellik</span><span class="sxs-lookup"><span data-stu-id="44ff9-111">Property</span></span>|<span data-ttu-id="44ff9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44ff9-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="44ff9-113">İfade</span><span class="sxs-lookup"><span data-stu-id="44ff9-113">Expression</span></span>|<span data-ttu-id="44ff9-114">İfade değerlendirilir ve çalışmaları listesinde aralıkları karşı karşılaştırıldığında budur.</span><span class="sxs-lookup"><span data-stu-id="44ff9-114">This is the expression to be evaluated and compared against the ranges in the Cases list.</span></span> <span data-ttu-id="44ff9-115">İfadenin sonucu t türüdür</span><span class="sxs-lookup"><span data-stu-id="44ff9-115">The result of the expression is of type T.</span></span>|  
|<span data-ttu-id="44ff9-116">Durumları</span><span class="sxs-lookup"><span data-stu-id="44ff9-116">Cases</span></span>|<span data-ttu-id="44ff9-117">Her durumda, bir aralığı (başlangıç ve bitiş) ve bir etkinlik (gövde) oluşur.</span><span class="sxs-lookup"><span data-stu-id="44ff9-117">Each case consists of a range (From and To) and an activity (Body).</span></span> <span data-ttu-id="44ff9-118">İfade değerlendirilir ve aralıkları karşı karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="44ff9-118">The expression is evaluated and compared against the ranges.</span></span> <span data-ttu-id="44ff9-119">İfadenin sonucu aralığı durumlarından biri içinde ise, karşılık gelen etkinlik yürütülür.</span><span class="sxs-lookup"><span data-stu-id="44ff9-119">If the result of the expression is within the range of one of the cases, the corresponding activity is executed.</span></span>|  
|<span data-ttu-id="44ff9-120">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="44ff9-120">Default</span></span>|<span data-ttu-id="44ff9-121">Hiçbir durum eşleştiğinde çalıştırılan etkinlik.</span><span class="sxs-lookup"><span data-stu-id="44ff9-121">The activity that is executed when no case is matched.</span></span> <span data-ttu-id="44ff9-122">Ayarlandığında `null`, hiçbir işlem yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="44ff9-122">When set to `null`, no action is taken.</span></span>|  
  
## <a name="caserange-class"></a><span data-ttu-id="44ff9-123">CaseRange sınıfı</span><span class="sxs-lookup"><span data-stu-id="44ff9-123">CaseRange Class</span></span>  
 <span data-ttu-id="44ff9-124">`CaseRange` Sınıfı temsil eder bir aralıkta bir `SwitchRange` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="44ff9-124">The `CaseRange` class represents a range within a `SwitchRange` activity.</span></span> <span data-ttu-id="44ff9-125">Her örneğini `CaseRange` bir aralık içerdiği (oluşan bir `From` ve `To`) ve bir `Body` , zamanlanmış etkinlik ifadesinde `SwitchRange` aralığında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="44ff9-125">Every instance of `CaseRange` contains a range (composed of a `From` and a `To`) and a `Body` activity that is scheduled if the expression in the `SwitchRange` is evaluated within the range.</span></span>  
  
 <span data-ttu-id="44ff9-126">Aşağıdaki kod örneği için tanımıdır `CaseRange` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="44ff9-126">The following code example is the definition for the `CaseRange` class.</span></span>  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="44ff9-127">Hem `SwitchRange` ve `CaseRange` örnekte tanımlanan sınıflar olan uygulayan herhangi bir tür ile çalışabilir Genel sınıflar `IComparable`gibi <xref:System.Activities.Statements.Switch%601> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="44ff9-127">Both the `SwitchRange` and `CaseRange` classes, which are defined in the sample are generic classes that can work with any type that implements `IComparable`, like the <xref:System.Activities.Statements.Switch%601> class.</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="44ff9-128">Örnek kullanımı</span><span class="sxs-lookup"><span data-stu-id="44ff9-128">Sample Usage</span></span>  
 <span data-ttu-id="44ff9-129">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir `SwitchRange` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="44ff9-129">The following code example demonstrates how to use the `SwitchRange` activity.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="44ff9-130">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="44ff9-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="44ff9-131">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], SwitchRange.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="44ff9-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the SwitchRange.sln solution file.</span></span>  
  
2.  <span data-ttu-id="44ff9-132">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="44ff9-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="44ff9-133">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="44ff9-133">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="44ff9-134">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="44ff9-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="44ff9-135">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="44ff9-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="44ff9-136">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="44ff9-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="44ff9-137">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="44ff9-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`