---
title: Yerel Kanal
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dee09b8f7b1e48a84fa79381d44fe48a4da16129
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="local-channel"></a><span data-ttu-id="5f049-102">Yerel Kanal</span><span class="sxs-lookup"><span data-stu-id="5f049-102">Local Channel</span></span>
<span data-ttu-id="5f049-103">Yerel kanal bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aynı uygulama etki alanı içinde iletişim için kullanılan taşıma kanalı.</span><span class="sxs-lookup"><span data-stu-id="5f049-103">Local Channel is a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="5f049-104">Burada istemci ve hizmet aynı uygulama etki alanında çalışan ve tipik WCF kanalı yığınının (seri hale getirme ve seri durumdan çıkarma iletilerinin) ek yükünü kaçınılmalıdır senaryoları için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="5f049-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5f049-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="5f049-105">Demonstrates</span></span>  
 <span data-ttu-id="5f049-106">Yerel Kanal</span><span class="sxs-lookup"><span data-stu-id="5f049-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="5f049-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="5f049-107">Discussion</span></span>  
 <span data-ttu-id="5f049-108">Örnek iki proje dosyaları içerir:</span><span class="sxs-lookup"><span data-stu-id="5f049-108">The sample consists of two project files:</span></span>  
  
-   <span data-ttu-id="5f049-109">**LocalChannel**: geçerli uygulama etki alanı içinde yerel kanal programlı gösterimi.</span><span class="sxs-lookup"><span data-stu-id="5f049-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="5f049-110">Bu projede gönderen bileşeni ileti bir bellek içi sıraya koyar ve alıcı bileşen alması iletiyi kuyruktan.</span><span class="sxs-lookup"><span data-stu-id="5f049-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
-   <span data-ttu-id="5f049-111">**ClientAndService**: Bu proje bir hizmeti bir konsol uygulamasında barındırır ve aynı uygulama etki alanı içinde hizmetinden çağırmak için bir istemci çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5f049-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="5f049-112">Yerel kanal tasarım kanal yığını ve hızını artırmak için seri hale getirme işlemi atlanıyor.</span><span class="sxs-lookup"><span data-stu-id="5f049-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="5f049-113">Yerel taşıma kanalı, bir kuyruk hizmeti için istemci hizmeti çağrıları taşıma ve istemciye geri dönüş değeri kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5f049-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="5f049-114">Parametreler ve dönüş değerleri serileştirme yerine örnek nesneleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="5f049-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5f049-115">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="5f049-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5f049-116">Derleme ve LocalChannel çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5f049-116">Build and run the LocalChannel solution.</span></span>  
  
2.  <span data-ttu-id="5f049-117">Hizmet ana bilgisayarı başlatılır ve istemcinin yerel kanal kullanarak hizmetini çağırır.</span><span class="sxs-lookup"><span data-stu-id="5f049-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="5f049-118">Hizmet arama sonuçlarını görüntülemek için bir konsol penceresi görünür.</span><span class="sxs-lookup"><span data-stu-id="5f049-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5f049-119">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5f049-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5f049-120">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5f049-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5f049-121">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5f049-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5f049-122">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5f049-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
