---
title: "InvokeMethod etkinliğini kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ba0c2333c14eaebdb6409323bb6b92aa2b29d2ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-invokemethod-activity"></a><span data-ttu-id="a986f-102">InvokeMethod etkinliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="a986f-102">Using the InvokeMethod Activity</span></span>
<span data-ttu-id="a986f-103">Bu örnek nasıl kullanılacağı ortaya <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) ortak sınıflarda ortak yöntemleri çağırmak için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a986f-103">This sample demonstrates how to use the <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity to invoke public methods in public classes.</span></span> <span data-ttu-id="a986f-104"><!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) Etkinlik nesneleri karşı yöntemlerini çağırın, parametreleri geçirin, dönüş değeri almak, genel yöntemler için türlerini belirtme ve yöntemi zaman uyumlu olup olmadığını belirlemek için iş akışı izin verir veya zaman uyumsuz.</span><span class="sxs-lookup"><span data-stu-id="a986f-104">The <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity allows a workflow to call methods against objects, pass in parameters, get the return value, specify types for generic methods, and specify whether the method is synchronous or asynchronous.</span></span> 
  
<span data-ttu-id="a986f-105">Genel olmayan sürümü <xref:System.Activities.Statements.InvokeMethod> için dönüş değerini ayarlandığı etkinlik <xref:System.Activities.Statements.InvokeMethod.Result%2A> özelliği ve genel bir sürümü <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) etkinlik burada dönüş değeri döndürülür aracılığıyla <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> --> [ <code>System.Activities.Statements.InvokeMethod\`1.Result</code> ](https://msdn.microsoft.com/library/dd987724.aspx) türündeki özelliği `TResult`.</span><span class="sxs-lookup"><span data-stu-id="a986f-105">There is a non-generic version of the <xref:System.Activities.Statements.InvokeMethod> activity where the return value is set to the <xref:System.Activities.Statements.InvokeMethod.Result%2A> property and a generic version of the <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity where the return value is returned through the <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> -->[<code>System.Activities.Statements.InvokeMethod\`1.Result</code>](https://msdn.microsoft.com/library/dd987724.aspx) property of type `TResult`.</span></span> 
  
 <span data-ttu-id="a986f-106">Bu örnek, çeşitli yöntemi türleri çağırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a986f-106">This sample demonstrates how to call various method types.</span></span> <span data-ttu-id="a986f-107">Aşağıdaki liste ayrıntıları yöntemi türleri bu örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a986f-107">The following list details the method types demonstrated in this sample:</span></span>  
  
-   <span data-ttu-id="a986f-108">Parametresiz bir örnek yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="a986f-108">Invoke an instance method without parameters.</span></span>  
  
-   <span data-ttu-id="a986f-109">Örnek yöntemi iki parametre (System.String ve System.Int32) ile çağırır.</span><span class="sxs-lookup"><span data-stu-id="a986f-109">Invoke an instance method with two parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="a986f-110">Örnek yöntemi iki parametre (System.String ve System.Int32) ve System.String [] türünde bir parametre dizisi ile çağırır.</span><span class="sxs-lookup"><span data-stu-id="a986f-110">Invoke an instance method with two parameters (System.String and System.Int32) and a parameter array of type System.String[].</span></span>  
  
-   <span data-ttu-id="a986f-111">Örnek yöntemi iki parametre (iki System.Int32 sayılar) ile ve bir sonuç türü System.Int32 çağırır.</span><span class="sxs-lookup"><span data-stu-id="a986f-111">Invoke an instance method with two parameters (two System.Int32 numbers) and a result of type System.Int32.</span></span>  
  
     <span data-ttu-id="a986f-112">Dönüş değeri bir değişkene bağlı ve konsolunu kullanarak yazdırılan <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a986f-112">The return value is bound to a variable and printed to the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
-   <span data-ttu-id="a986f-113">İki parametre (System.String ve System.Int32) ile statik bir yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="a986f-113">Invoke a static method with two parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="a986f-114">Bir genel parametre (System.String) ile örnek yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="a986f-114">Invoke an instance method with one generic parameter (System.String).</span></span>  
  
-   <span data-ttu-id="a986f-115">İki genel parametreleri (System.String ve System.Int32) olan bir statik yöntem çağırır.</span><span class="sxs-lookup"><span data-stu-id="a986f-115">Invoke a static method with two generic parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="a986f-116">Başvuru (System.String) tarafından geçirilen bir parametre olan örnek yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="a986f-116">Invoke an instance method that has one parameter passed by reference (System.String).</span></span>  
  
     <span data-ttu-id="a986f-117">Başvurulan parametresi bir değişkene bağlı ve konsolunu kullanarak yazdırılan <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a986f-117">The referenced parameter is bound to a variable and printed to the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
-   <span data-ttu-id="a986f-118">Zaman uyumsuz örnek yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="a986f-118">Invoke an asynchronous instance method.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="a986f-119">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="a986f-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="a986f-120">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], InvokeMethodUsage.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="a986f-120">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a986f-121">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a986f-121">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a986f-122">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a986f-122">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a986f-123">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a986f-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a986f-124">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a986f-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a986f-125">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a986f-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a986f-126">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a986f-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`