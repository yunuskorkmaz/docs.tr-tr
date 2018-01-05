---
title: "RangeEnumeration etkinliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7dc793d57718dbc68f304d3eb5031a9fa96b00cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="rangeenumeration-activity"></a><span data-ttu-id="fa15e-102">RangeEnumeration etkinliği</span><span class="sxs-lookup"><span data-stu-id="fa15e-102">RangeEnumeration Activity</span></span>
<span data-ttu-id="fa15e-103">Bu örnek nasıl sayıların bir koleksiyon yineleme özel bir aktivite oluşturulacağını gösterir. Aşağıdaki tabloda örnek bulunan ana dosyalar ayrıntılarını verir.</span><span class="sxs-lookup"><span data-stu-id="fa15e-103">This sample demonstrates how to create a custom activity that iterates over a collection of numbers.The following table details the main files included in the sample.</span></span>  
  
|<span data-ttu-id="fa15e-104">Dosya adı</span><span class="sxs-lookup"><span data-stu-id="fa15e-104">File name</span></span>|<span data-ttu-id="fa15e-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa15e-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fa15e-106">RangeEnumeration.cs</span><span class="sxs-lookup"><span data-stu-id="fa15e-106">RangeEnumeration.cs</span></span>|<span data-ttu-id="fa15e-107">Adlı özel bir aktivite tanımlar `RangeEnumeration` , geçersiz kılmalar <xref:System.Activities.NativeActivity> sınıfı ve bir dizi numarası aracılığıyla döngüleri.</span><span class="sxs-lookup"><span data-stu-id="fa15e-107">Defines a custom activity named `RangeEnumeration` that overrides the <xref:System.Activities.NativeActivity> class and loops through a series of numbers.</span></span>|  
|<span data-ttu-id="fa15e-108">RangeEnumerationSample.cs</span><span class="sxs-lookup"><span data-stu-id="fa15e-108">RangeEnumerationSample.cs</span></span>|<span data-ttu-id="fa15e-109">Kullanan bir istemci uygulaması `RangeEnumeration` sayıların koleksiyon üzerinde yinelenecek etkinlik.</span><span class="sxs-lookup"><span data-stu-id="fa15e-109">A client application that uses the `RangeEnumeration` activity to iterate over a collection of numbers.</span></span>|  
  
 <span data-ttu-id="fa15e-110">Aşağıdaki tabloda özelliklerini ayrıntıları `RangeEnumeration` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="fa15e-110">The following table details the properties of the `RangeEnumeration` activity.</span></span>  
  
|<span data-ttu-id="fa15e-111">Özellik</span><span class="sxs-lookup"><span data-stu-id="fa15e-111">Property</span></span>|<span data-ttu-id="fa15e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa15e-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="fa15e-113">Başlat</span><span class="sxs-lookup"><span data-stu-id="fa15e-113">Start</span></span>|<span data-ttu-id="fa15e-114">Döngüden başlatmak için tam sayı.</span><span class="sxs-lookup"><span data-stu-id="fa15e-114">The integer to start the loop from.</span></span>|  
|<span data-ttu-id="fa15e-115">Durdur</span><span class="sxs-lookup"><span data-stu-id="fa15e-115">Stop</span></span>|<span data-ttu-id="fa15e-116">Döngü sırasında durdurmak için bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="fa15e-116">The integer to stop the loop at.</span></span>|  
|<span data-ttu-id="fa15e-117">Adım</span><span class="sxs-lookup"><span data-stu-id="fa15e-117">Step</span></span>|<span data-ttu-id="fa15e-118">Her zaman yinelemek için ne kadar belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa15e-118">Specifies how much to iterate each time.</span></span>|  
|<span data-ttu-id="fa15e-119">Gövde</span><span class="sxs-lookup"><span data-stu-id="fa15e-119">Body</span></span>|<span data-ttu-id="fa15e-120">Her yineleme sırasında yürütülecek kod belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa15e-120">Specifies the code to execute during each iteration.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="fa15e-121">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="fa15e-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="fa15e-122">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], RangeEnumeration.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="fa15e-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RangeEnumeration.sln solution file.</span></span>  
  
2.  <span data-ttu-id="fa15e-123">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fa15e-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="fa15e-124">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fa15e-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fa15e-125">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="fa15e-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fa15e-126">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fa15e-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fa15e-127">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="fa15e-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fa15e-128">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fa15e-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`