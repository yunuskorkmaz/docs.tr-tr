---
title: RangeEnumeration etkinliği
ms.date: 03/30/2017
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
ms.openlocfilehash: c9cf522227620422b414adc26cbc0bf338bf57d4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868724"
---
# <a name="rangeenumeration-activity"></a><span data-ttu-id="18ed8-102">RangeEnumeration etkinliği</span><span class="sxs-lookup"><span data-stu-id="18ed8-102">RangeEnumeration Activity</span></span>
<span data-ttu-id="18ed8-103">Bu örnek, sayıdan oluşan bir koleksiyon yineleme özel bir etkinlik oluşturma işlemini gösterir. Aşağıdaki tabloda, örnekte bulunan ana dosyaları ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="18ed8-103">This sample demonstrates how to create a custom activity that iterates over a collection of numbers.The following table details the main files included in the sample.</span></span>  
  
|<span data-ttu-id="18ed8-104">Dosya adı</span><span class="sxs-lookup"><span data-stu-id="18ed8-104">File name</span></span>|<span data-ttu-id="18ed8-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18ed8-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18ed8-106">RangeEnumeration.cs</span><span class="sxs-lookup"><span data-stu-id="18ed8-106">RangeEnumeration.cs</span></span>|<span data-ttu-id="18ed8-107">Adlı özel bir etkinlik tanımlar `RangeEnumeration` , geçersiz kılmalar <xref:System.Activities.NativeActivity> sınıfı ve bir dizi numarası döner.</span><span class="sxs-lookup"><span data-stu-id="18ed8-107">Defines a custom activity named `RangeEnumeration` that overrides the <xref:System.Activities.NativeActivity> class and loops through a series of numbers.</span></span>|  
|<span data-ttu-id="18ed8-108">RangeEnumerationSample.cs</span><span class="sxs-lookup"><span data-stu-id="18ed8-108">RangeEnumerationSample.cs</span></span>|<span data-ttu-id="18ed8-109">Kullanan bir istemci uygulamanın `RangeEnumeration` sayıdan oluşan bir koleksiyon üzerinde yinelemek için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="18ed8-109">A client application that uses the `RangeEnumeration` activity to iterate over a collection of numbers.</span></span>|  
  
 <span data-ttu-id="18ed8-110">Aşağıdaki tabloda özelliklerine ilişkin ayrıntılar `RangeEnumeration` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="18ed8-110">The following table details the properties of the `RangeEnumeration` activity.</span></span>  
  
|<span data-ttu-id="18ed8-111">Özellik</span><span class="sxs-lookup"><span data-stu-id="18ed8-111">Property</span></span>|<span data-ttu-id="18ed8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18ed8-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="18ed8-113">Başlat</span><span class="sxs-lookup"><span data-stu-id="18ed8-113">Start</span></span>|<span data-ttu-id="18ed8-114">Döngüden başlatmak için bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="18ed8-114">The integer to start the loop from.</span></span>|  
|<span data-ttu-id="18ed8-115">Durdur</span><span class="sxs-lookup"><span data-stu-id="18ed8-115">Stop</span></span>|<span data-ttu-id="18ed8-116">Döngü, durdurmak için bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="18ed8-116">The integer to stop the loop at.</span></span>|  
|<span data-ttu-id="18ed8-117">Adım</span><span class="sxs-lookup"><span data-stu-id="18ed8-117">Step</span></span>|<span data-ttu-id="18ed8-118">Her yineleme yapmak için ne kadar belirtir.</span><span class="sxs-lookup"><span data-stu-id="18ed8-118">Specifies how much to iterate each time.</span></span>|  
|<span data-ttu-id="18ed8-119">Gövde</span><span class="sxs-lookup"><span data-stu-id="18ed8-119">Body</span></span>|<span data-ttu-id="18ed8-120">Her yineleme sırasında yürütülecek kodu belirtir.</span><span class="sxs-lookup"><span data-stu-id="18ed8-120">Specifies the code to execute during each iteration.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="18ed8-121">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="18ed8-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="18ed8-122">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], RangeEnumeration.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="18ed8-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RangeEnumeration.sln solution file.</span></span>  
  
2.  <span data-ttu-id="18ed8-123">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="18ed8-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="18ed8-124">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="18ed8-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="18ed8-125">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="18ed8-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="18ed8-126">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="18ed8-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="18ed8-127">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="18ed8-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="18ed8-128">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="18ed8-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`