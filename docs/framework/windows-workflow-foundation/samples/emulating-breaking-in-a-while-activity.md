---
title: Bir süre sonu öykünen etkinliği
ms.date: 03/30/2017
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
ms.openlocfilehash: 37c64c2b8dc03d58f9c2802edef644fe4888e87d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514719"
---
# <a name="emulating-breaking-in-a-while-activity"></a><span data-ttu-id="f1ba5-102">Bir süre sonu öykünen etkinliği</span><span class="sxs-lookup"><span data-stu-id="f1ba5-102">Emulating breaking in a While activity</span></span>
<span data-ttu-id="f1ba5-103">Bu örnek, aşağıdaki etkinliklerin döngü mekanizması ayırmak gösterilmiştir: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, ve <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="f1ba5-103">This sample demonstrates how to break the looping mechanism of the following activities: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span>  
  
 <span data-ttu-id="f1ba5-104">Windows Workflow Foundation (WF) bu döngüler yürütülmesi ayırmak için herhangi bir etkinlik içermediğinden bu yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="f1ba5-104">This is useful because Windows Workflow Foundation (WF) does not include any activity to break the execution of these loops.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="f1ba5-105">Senaryo</span><span class="sxs-lookup"><span data-stu-id="f1ba5-105">Scenario</span></span>  
 <span data-ttu-id="f1ba5-106">Örnek satıcılarının listesini ilk güvenilir satıcıdan bulur (örneklerini `Vendor` sınıfı).</span><span class="sxs-lookup"><span data-stu-id="f1ba5-106">The sample finds the first reliable vendor from a list of vendors (instances of the `Vendor` class).</span></span> <span data-ttu-id="f1ba5-107">Her satıcının bulunan bir `ID`, `Name` ve nasıl güvenilir satıcı mi belirleyen sayısal güvenilirlik değer.</span><span class="sxs-lookup"><span data-stu-id="f1ba5-107">Each vendor has an `ID`, a `Name` and a numeric reliability value that determines how dependable the vendor is.</span></span> <span data-ttu-id="f1ba5-108">Örnek olarak adlandırılan özel bir etkinlik oluşturur `FindReliableVendor` , iki giriş parametreleri (Satıcılar ve en düşük güvenilirlik değer listesi) alır ve sağlanan ölçütlerle eşleşen listedeki ilk satıcısına döndürür.</span><span class="sxs-lookup"><span data-stu-id="f1ba5-108">The sample creates a custom activity called `FindReliableVendor` that receives two input parameters (a list of vendors and a minimum reliability value) and returns the first vendor of the list that matches the supplied criteria.</span></span>  
  
## <a name="breaking-a-loop"></a><span data-ttu-id="f1ba5-109">Döngü kesiliyor</span><span class="sxs-lookup"><span data-stu-id="f1ba5-109">Breaking a Loop</span></span>  
 <span data-ttu-id="f1ba5-110">Windows Workflow Foundation (WF) bir döngüsünü kesmek için bir etkinlik içermez.</span><span class="sxs-lookup"><span data-stu-id="f1ba5-110">Windows Workflow Foundation (WF) does not include an activity to break a loop.</span></span> <span data-ttu-id="f1ba5-111">Kod örneği kullanarak bir döngü çiğnemekten gerçekleştirir bir <xref:System.Activities.Statements.If> etkinliği ve çeşitli değişkenler.</span><span class="sxs-lookup"><span data-stu-id="f1ba5-111">The code sample accomplishes breaking a loop by using an <xref:System.Activities.Statements.If> activity and several variables.</span></span> <span data-ttu-id="f1ba5-112">Örnekte, <xref:System.Activities.Statements.While> etkinlik bozulur kez `reliableVendor` değişkeni atanan değer dışında `null`.</span><span class="sxs-lookup"><span data-stu-id="f1ba5-112">In the sample, the <xref:System.Activities.Statements.While> activity is broken once the `reliableVendor` variable is assigned a value other than `null`.</span></span>  
  
 <span data-ttu-id="f1ba5-113">Aşağıdaki kod örneğinde nasıl örnek biraz keser gösterilmektedir döngü.</span><span class="sxs-lookup"><span data-stu-id="f1ba5-113">The following code example demonstrates how the sample breaks a while loop.</span></span>  
  
```csharp  
// Iterates while the "i" variable is lower than the size of the list   
// and any reliable Vendor is found.        
new While(env => i.Get(env) < this.Vendors.Get(env).Count && reliableVendor.Get(env) == null)  
{  
    DisplayName = "Main loop. Breaks when a reliable vendor is found",  
    Body = new Sequence  
    {                              
        Activities =  
        {  
            // This is the if used for setting the value of the break value…  
            new If  
            {  
                DisplayName = "Check for a reliable vendor",  
  
                //  If a vendor satisfies the reliability level…  
                Condition = new InArgument<bool>(env =>   
                           this.Vendors.Get(env)[i.Get(env)].Reliability >   
                           this.MinimumReliability.Get(env)),  
  
                // then assign that vendor to the reliable vendor variable and   
                // the while condition becomes false (exit the loop).  
                Then = new Assign<Vendor>  
                {  
                    To = reliableVendor,  
                    Value = new InArgument<Vendor>(env =>   
                                  this.Vendors.Get(env)[i.Get(env)])  
                }  
            },  
  
            // Increment the iteration variable.   
            new Assign<int>  
            {  
                DisplayName = "Increment iteration variable",  
                To = i,  
                Value = new InArgument<int>(env => i.Get(env) + 1)  
            }   
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f1ba5-114">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="f1ba5-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="f1ba5-115">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], EmulatingBreakInWhile.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="f1ba5-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the EmulatingBreakInWhile.sln solution file.</span></span>  
  
2.  <span data-ttu-id="f1ba5-116">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f1ba5-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="f1ba5-117">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f1ba5-117">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f1ba5-118">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f1ba5-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f1ba5-119">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f1ba5-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f1ba5-120">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="f1ba5-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f1ba5-121">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f1ba5-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`