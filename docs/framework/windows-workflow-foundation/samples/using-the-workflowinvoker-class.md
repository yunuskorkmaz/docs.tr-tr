---
title: "WorkflowInvoker sınıfını kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 553367916ff249118a8fcdd8273382402b90cfcc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-workflowinvoker-class"></a><span data-ttu-id="091ff-102">WorkflowInvoker sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="091ff-102">Using the WorkflowInvoker Class</span></span>
<span data-ttu-id="091ff-103">Bu örnek nasıl kullanılacağı ortaya <xref:System.Activities.WorkflowInvoker> bir yöntem değilmiş gibi bir etkinlik çağrılacak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="091ff-103">This sample demonstrates how to use the <xref:System.Activities.WorkflowInvoker> class to invoke an activity as if it were a method.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="091ff-104">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="091ff-104">Sample Details</span></span>  
 <span data-ttu-id="091ff-105">Kullanarak <xref:System.Activities.WorkflowInvoker> bir aktivite çalıştırmak için en basit yolu bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="091ff-105">Using the <xref:System.Activities.WorkflowInvoker> class is the simplest way to execute an activity.</span></span> <span data-ttu-id="091ff-106">Yöntem çağrısı değilmiş gibi doğrudan bir aktivite çalıştırmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="091ff-106">It is designed for directly running an activity as if it were a method call.</span></span> <span data-ttu-id="091ff-107">Burada bir etkinliğin yürütme barındırma diğer Çeşitleme tarafından sağlanan denetim altyapı gerektirmez senaryolarda kullanım için basit, yüksek performanslı, kullanımı kolay bir API değil.</span><span class="sxs-lookup"><span data-stu-id="091ff-107">It is a lightweight, high-performing, easy to use API for use in scenarios where an activity’s execution does not require the control infrastructure provided by other hosting variations.</span></span>  
  
 <span data-ttu-id="091ff-108">Örnek türetilen özel bir aktivite kullanır <xref:System.Activities.CodeActivity%601>< Int32\> adlı `Add` iki ekleyen <xref:System.Activities.InArgument%601>, `X` ve `Y`ve döndüren bir `Result` <xref:System.Activities.OutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="091ff-108">The sample uses a custom activity that derives from <xref:System.Activities.CodeActivity%601><Int32\> named `Add` that adds two <xref:System.Activities.InArgument%601>, `X` and `Y`, and returns a `Result`<xref:System.Activities.OutArgument%601>.</span></span> <span data-ttu-id="091ff-109">(<xref:System.Activities.CodeActivity%601>\<T > türetilen <xref:System.Activities.Activity%601>< T\>, sahip olduğu bir <xref:System.Activities.OutArgument%601> \<T > adlı `Result`.) A `Dictionary` \<dize, Nesne > bağımsız değişkenleri aracılığıyla çağrılan etkinliğe geçirmek için kullanılan <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="091ff-109">(<xref:System.Activities.CodeActivity%601>\<T> derives from <xref:System.Activities.Activity%601><T\>, which has an <xref:System.Activities.OutArgument%601>\<T> named `Result`.) A `Dictionary`\<string, object> is used to pass arguments into an activity being invoked through <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="091ff-110">Anahtarı sözlük çağrılan etkinlik bağımsız değişken adını karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="091ff-110">The key of the dictionary corresponds to the name of an argument on the invoked activity.</span></span> <span data-ttu-id="091ff-111">Belirli bir anahtarla ilişkilendirilen değeri anahtarı tarafından tanımlanan bağımsız değişkeni bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="091ff-111">The value associated with a particular key is bound to the argument identified by the key.</span></span>  
  
 <span data-ttu-id="091ff-112">Örnek aramalar <xref:System.Activities.WorkflowInvoker.Invoke%2A> ve değerlerini içeren bir sözlük geçirir `X` ve `Y`.</span><span class="sxs-lookup"><span data-stu-id="091ff-112">The sample calls <xref:System.Activities.WorkflowInvoker.Invoke%2A> and passes a dictionary that contains values for `X` and `Y`.</span></span> <span data-ttu-id="091ff-113"><xref:System.Activities.WorkflowInvoker> Sınıfı bu değerleri bağlar `Add` etkinlik bağımsız değişkenlerini kullanıcının, etkinlik yürütür ve sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="091ff-113">The <xref:System.Activities.WorkflowInvoker> class binds these values to the `Add` activity’s arguments, executes the activity, and returns the result.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="091ff-114">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="091ff-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="091ff-115">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], Invoker.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="091ff-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Invoker.sln solution file.</span></span>  
  
2.  <span data-ttu-id="091ff-116">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="091ff-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="091ff-117">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="091ff-117">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="091ff-118">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="091ff-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="091ff-119">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="091ff-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="091ff-120">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="091ff-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="091ff-121">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="091ff-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`