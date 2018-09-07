---
title: InvokeMethod
ms.date: 03/30/2017
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
ms.openlocfilehash: 861e0cf160aec9814abcf8c27c37ce13a5d88b2a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047717"
---
# <a name="invokemethod"></a><span data-ttu-id="ab5b9-102">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="ab5b9-102">InvokeMethod</span></span>
<span data-ttu-id="ab5b9-103">Bu örnek, kullanarak farklı yollarını gösterir. <xref:System.Activities.Statements.InvokeMethod> sınıfının yöntemlerini çağırmak için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-103">This sample shows the different ways of using the <xref:System.Activities.Statements.InvokeMethod> activity to invoke methods of a class.</span></span>  
  
 <span data-ttu-id="ab5b9-104">Bir yöntem, bir sınıfa aittir ve kapsanan bir işlemler kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-104">A method belongs to a class and represents a contained set of operations.</span></span> <span data-ttu-id="ab5b9-105"><xref:System.Activities.Statements.InvokeMethod> Etkinlik nesneleri veya türlerine karşı yöntemleri çağırmak, parametreleri geçirin ve dönüş değeri elde etmek için yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-105">The <xref:System.Activities.Statements.InvokeMethod> activity gives you the ability to call methods against objects or types, pass in parameters, and get the return value.</span></span> <span data-ttu-id="ab5b9-106">Yöntemler, zaman uyumlu veya zaman uyumsuz olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-106">Methods can be invoked synchronously or asynchronously.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="ab5b9-107">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="ab5b9-107">Sample Details</span></span>  
 <span data-ttu-id="ab5b9-108">Bu örnekte <xref:System.Activities.Statements.InvokeMethod> etkinlik aşağıdaki senaryoları gerçekleştirmek için:</span><span class="sxs-lookup"><span data-stu-id="ab5b9-108">This sample uses the <xref:System.Activities.Statements.InvokeMethod> activity to perform the following scenarios:</span></span>  
  
1.  <span data-ttu-id="ab5b9-109">Parametresiz örnek yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-109">Invoke an instance method without parameters.</span></span>  
  
2.  <span data-ttu-id="ab5b9-110">İki parametre ile bir örnek yöntemi çağırma (<xref:System.String> ve <xref:System.Int32>).</span><span class="sxs-lookup"><span data-stu-id="ab5b9-110">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>).</span></span>  
  
3.  <span data-ttu-id="ab5b9-111">İki parametre ile bir örnek yöntemi çağırma (<xref:System.String> ve <xref:System.Int32>) ve türünde bir parametre dizisi <xref:System.String>[].</span><span class="sxs-lookup"><span data-stu-id="ab5b9-111">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>) and a parameter array of type <xref:System.String>[].</span></span>  
  
4.  <span data-ttu-id="ab5b9-112">Türünde iki parametre ile bir örnek yöntemi Çağır <xref:System.Int32> ve bir sonuç türü <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-112">Invoke an instance method with two parameters of type <xref:System.Int32> and a result of type <xref:System.Int32>.</span></span> <span data-ttu-id="ab5b9-113">Bu senaryoda, sonuç değeri bir değişkene bağımlı ve başka bir etkinlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-113">In this scenario, the result value is bound to a variable and used in another activity.</span></span> <span data-ttu-id="ab5b9-114">Konsolunu kullanarak görüntülenir <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-114">It is displayed in the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
5.  <span data-ttu-id="ab5b9-115">Türünde iki parametre ile statik bir yöntemi çağırmak <xref:System.String> ve <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-115">Invoke a static method with two parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
6.  <span data-ttu-id="ab5b9-116">Bir genel tür parametresi ile bir örnek yöntemi Çağır <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-116">Invoke an instance method with one generic parameter of type <xref:System.String>.</span></span>  
  
7.  <span data-ttu-id="ab5b9-117">İki genel tür parametreleri ile statik bir yöntemi çağırmak <xref:System.String> ve <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-117">Invoke a static method with two generic parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
8.  <span data-ttu-id="ab5b9-118">Bir parametre türü bir başvuru tarafından geçirilmediğine sahip bir örnek yöntemi Çağır <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-118">Invoke an instance method that has one parameter passed by reference of type <xref:System.String>.</span></span> <span data-ttu-id="ab5b9-119">Bu senaryoda, başvuru parametresi bir değişkene bağlıdır (`outParam`) ve başka bir etkinlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-119">In this scenario, the reference parameter is bound to a variable (`outParam`) and used in another activity.</span></span> <span data-ttu-id="ab5b9-120">Konsolunu kullanarak görüntülenir <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-120">It is displayed on the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
9. <span data-ttu-id="ab5b9-121">Bir zaman uyumsuz örnek yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-121">Invoke an asynchronous instance method.</span></span>  
  
10. <span data-ttu-id="ab5b9-122">Kullanarak iki nesnenin aynı örneğinde iki farklı yöntem çağırma <xref:System.Activities.Statements.InvokeMethod> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-122">Invoke two different methods on the same instance of an object using two <xref:System.Activities.Statements.InvokeMethod> activities.</span></span>  
  
11. <span data-ttu-id="ab5b9-123">Değer bir nesne örneğini Store.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-123">Store a value in an instance of an object.</span></span>  
  
12. <span data-ttu-id="ab5b9-124">Bir nesnenin bir örneğinden bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-124">Retrieve a value from an instance of an object.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="ab5b9-125">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="ab5b9-125">To use this sample</span></span>  
 <span data-ttu-id="ab5b9-126">Bu örnek, iki sürümde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-126">This sample is provided in two versions.</span></span> <span data-ttu-id="ab5b9-127">İlk sürümü bu örnek kullanımını gösterir <xref:System.Activities.Statements.InvokeMethod> C# ile kodlayın Windows Workflow Foundation (WF) programlama modelini kullanarak ve CodedWorkflow\CS klasörü altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-127">The first version of this sample demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> through C# code using the Windows Workflow Foundation (WF) programming model and can be found under the CodedWorkflow\CS folder.</span></span> <span data-ttu-id="ab5b9-128">Dosyanın ikinci sürümü kullanımını gösteren <xref:System.Activities.Statements.InvokeMethod> XAML kullanarak ve DesignerWorkflow\CS klasörü altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-128">The second version demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> using XAML and can be found under the DesignerWorkflow\CS folder.</span></span>  
  
#### <a name="to-run-the-coded-workflow-sample"></a><span data-ttu-id="ab5b9-129">Kodlanmış bir iş akışı örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ab5b9-129">To run the coded workflow sample</span></span>  
  
1.  <span data-ttu-id="ab5b9-130">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CodedWorkflow\CS klasöründe InvokeMethodUsage.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-130">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the CodedWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="ab5b9-131">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-131">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="ab5b9-132">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-132">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-run-the-designer-workflow-sample"></a><span data-ttu-id="ab5b9-133">Tasarımcı iş akışı örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ab5b9-133">To run the designer workflow sample</span></span>  
  
1.  <span data-ttu-id="ab5b9-134">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], DesignerWorkflow\CS klasöründe InvokeMethodUsage.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-134">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the DesignerWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="ab5b9-135">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-135">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="ab5b9-136">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-136">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ab5b9-137">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ab5b9-138">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ab5b9-139">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ab5b9-140">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`