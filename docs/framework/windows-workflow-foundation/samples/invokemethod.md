---
title: InvokeMethod
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0fc081f4958420b7f3a1236441f33cf124dade54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="invokemethod"></a><span data-ttu-id="7b20a-102">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="7b20a-102">InvokeMethod</span></span>
<span data-ttu-id="7b20a-103">Bu örnek kullanarak farklı yollarını gösterir <xref:System.Activities.Statements.InvokeMethod> bir sınıfın yöntemleri çağırmak için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="7b20a-103">This sample shows the different ways of using the <xref:System.Activities.Statements.InvokeMethod> activity to invoke methods of a class.</span></span>  
  
 <span data-ttu-id="7b20a-104">Bir yöntem bir sınıfa ait ve içerdiği bir işlemler kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7b20a-104">A method belongs to a class and represents a contained set of operations.</span></span> <span data-ttu-id="7b20a-105"><xref:System.Activities.Statements.InvokeMethod> Etkinlik, nesneler veya türleri karşı yöntemlerini çağırın, parametreleri geçirin ve dönüş değerini alma olanağı verir.</span><span class="sxs-lookup"><span data-stu-id="7b20a-105">The <xref:System.Activities.Statements.InvokeMethod> activity gives you the ability to call methods against objects or types, pass in parameters, and get the return value.</span></span> <span data-ttu-id="7b20a-106">Yöntemleri zaman uyumlu veya zaman uyumsuz olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="7b20a-106">Methods can be invoked synchronously or asynchronously.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="7b20a-107">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="7b20a-107">Sample Details</span></span>  
 <span data-ttu-id="7b20a-108">Bu örnekte <xref:System.Activities.Statements.InvokeMethod> aşağıdaki senaryolarda gerçekleştirme etkinliği:</span><span class="sxs-lookup"><span data-stu-id="7b20a-108">This sample uses the <xref:System.Activities.Statements.InvokeMethod> activity to perform the following scenarios:</span></span>  
  
1.  <span data-ttu-id="7b20a-109">Parametresiz bir örnek yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="7b20a-109">Invoke an instance method without parameters.</span></span>  
  
2.  <span data-ttu-id="7b20a-110">Örnek yöntemi iki parametre ile çağırma (<xref:System.String> ve <xref:System.Int32>).</span><span class="sxs-lookup"><span data-stu-id="7b20a-110">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>).</span></span>  
  
3.  <span data-ttu-id="7b20a-111">Örnek yöntemi iki parametre ile çağırma (<xref:System.String> ve <xref:System.Int32>) ve bir parametre dizisi türü <xref:System.String>[].</span><span class="sxs-lookup"><span data-stu-id="7b20a-111">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>) and a parameter array of type <xref:System.String>[].</span></span>  
  
4.  <span data-ttu-id="7b20a-112">Örnek yöntemi iki parametre türü ile çağırma <xref:System.Int32> ve bir sonuç türü <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="7b20a-112">Invoke an instance method with two parameters of type <xref:System.Int32> and a result of type <xref:System.Int32>.</span></span> <span data-ttu-id="7b20a-113">Bu senaryoda, sonuç değeri bir değişkene bağlı ve başka bir etkinliğin kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7b20a-113">In this scenario, the result value is bound to a variable and used in another activity.</span></span> <span data-ttu-id="7b20a-114">Konsolunu kullanarak görüntülenir <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="7b20a-114">It is displayed in the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
5.  <span data-ttu-id="7b20a-115">Türünde iki parametre ile bir statik yöntem çağırma <xref:System.String> ve <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="7b20a-115">Invoke a static method with two parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
6.  <span data-ttu-id="7b20a-116">Türünde bir genel parametresi ile örnek yöntemi çağırma <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="7b20a-116">Invoke an instance method with one generic parameter of type <xref:System.String>.</span></span>  
  
7.  <span data-ttu-id="7b20a-117">Türünde iki genel parametreleri olan bir statik yöntem çağırma <xref:System.String> ve <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="7b20a-117">Invoke a static method with two generic parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
8.  <span data-ttu-id="7b20a-118">Başvuru türü tarafından geçirilen bir parametre olan örnek yöntemi çağırma <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="7b20a-118">Invoke an instance method that has one parameter passed by reference of type <xref:System.String>.</span></span> <span data-ttu-id="7b20a-119">Bu senaryoda, bir değişkene başvuru parametresine bağlıdır (`outParam`) ve başka bir etkinliğin kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7b20a-119">In this scenario, the reference parameter is bound to a variable (`outParam`) and used in another activity.</span></span> <span data-ttu-id="7b20a-120">Konsolunu kullanarak görüntülenir <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="7b20a-120">It is displayed on the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
9. <span data-ttu-id="7b20a-121">Zaman uyumsuz örnek yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="7b20a-121">Invoke an asynchronous instance method.</span></span>  
  
10. <span data-ttu-id="7b20a-122">Aynı örneği iki kullanan bir nesne üzerinde iki farklı yöntem çağırma <xref:System.Activities.Statements.InvokeMethod> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="7b20a-122">Invoke two different methods on the same instance of an object using two <xref:System.Activities.Statements.InvokeMethod> activities.</span></span>  
  
11. <span data-ttu-id="7b20a-123">Bir değer bir nesne örneğini depolar.</span><span class="sxs-lookup"><span data-stu-id="7b20a-123">Store a value in an instance of an object.</span></span>  
  
12. <span data-ttu-id="7b20a-124">Bir nesnenin bir örnekten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="7b20a-124">Retrieve a value from an instance of an object.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="7b20a-125">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="7b20a-125">To use this sample</span></span>  
 <span data-ttu-id="7b20a-126">Bu örnek iki sürümlerinde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="7b20a-126">This sample is provided in two versions.</span></span> <span data-ttu-id="7b20a-127">Bu örnek ilk sürümü kullanımını gösteren <xref:System.Activities.Statements.InvokeMethod> C# ile kullanarak kod [!INCLUDE[wf](../../../../includes/wf-md.md)] programlama modeli ve CodedWorkflow\CS klasörü altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="7b20a-127">The first version of this sample demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> through C# code using the [!INCLUDE[wf](../../../../includes/wf-md.md)] programming model and can be found under the CodedWorkflow\CS folder.</span></span> <span data-ttu-id="7b20a-128">İkinci Sürüm kullanımını gösteren <xref:System.Activities.Statements.InvokeMethod> XAML kullanılarak ve DesignerWorkflow\CS klasörü altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="7b20a-128">The second version demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> using XAML and can be found under the DesignerWorkflow\CS folder.</span></span>  
  
#### <a name="to-run-the-coded-workflow-sample"></a><span data-ttu-id="7b20a-129">Kodlanmış iş akışı örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7b20a-129">To run the coded workflow sample</span></span>  
  
1.  <span data-ttu-id="7b20a-130">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CodedWorkflow\CS klasöründeki InvokeMethodUsage.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="7b20a-130">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the CodedWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="7b20a-131">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7b20a-131">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="7b20a-132">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7b20a-132">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-run-the-designer-workflow-sample"></a><span data-ttu-id="7b20a-133">Tasarımcı iş akışı örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7b20a-133">To run the designer workflow sample</span></span>  
  
1.  <span data-ttu-id="7b20a-134">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], DesignerWorkflow\CS klasöründeki InvokeMethodUsage.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="7b20a-134">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the DesignerWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="7b20a-135">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7b20a-135">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="7b20a-136">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7b20a-136">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7b20a-137">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7b20a-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7b20a-138">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7b20a-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7b20a-139">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7b20a-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b20a-140">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7b20a-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`  
  
## <a name="see-also"></a><span data-ttu-id="7b20a-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b20a-141">See Also</span></span>
