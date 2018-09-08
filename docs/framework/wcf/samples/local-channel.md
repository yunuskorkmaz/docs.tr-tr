---
title: Yerel Kanal
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 731fcfde52a6b1277551f7d70f795c721fc99dd8
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44136714"
---
# <a name="local-channel"></a><span data-ttu-id="d6f43-102">Yerel Kanal</span><span class="sxs-lookup"><span data-stu-id="d6f43-102">Local Channel</span></span>
<span data-ttu-id="d6f43-103">Yerel kanal aynı uygulama etki alanı içinde iletişim kurmak için kullanılan bir Windows Communication Foundation (WCF) aktarım kanalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6f43-103">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="d6f43-104">Burada aynı uygulama etki alanında çalışan istemci ve hizmet ve ek yükü tipik WCF kanalı yığınının (seri hale getirme ve seri durumundan çıkarma iletilerinin) kaçınılmalıdır senaryoları için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d6f43-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d6f43-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="d6f43-105">Demonstrates</span></span>  
 <span data-ttu-id="d6f43-106">Yerel Kanal</span><span class="sxs-lookup"><span data-stu-id="d6f43-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="d6f43-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="d6f43-107">Discussion</span></span>  
 <span data-ttu-id="d6f43-108">Örnek, iki proje dosyaları içerir:</span><span class="sxs-lookup"><span data-stu-id="d6f43-108">The sample consists of two project files:</span></span>  
  
-   <span data-ttu-id="d6f43-109">**LocalChannel**: geçerli uygulama etki alanı içinde yerel kanal programlı temsili.</span><span class="sxs-lookup"><span data-stu-id="d6f43-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="d6f43-110">Bu projede gönderen bileşeni bellek içi kuyruğu ileti yerleştirir ve alıcı bileşen alması iletiyi kuyruktan.</span><span class="sxs-lookup"><span data-stu-id="d6f43-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
-   <span data-ttu-id="d6f43-111">**ClientAndService**: Bu proje bir hizmeti bir konsol uygulamasında barındırır ve aynı uygulama etki alanı içinde hizmetini çağırmak için bir istemci çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="d6f43-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="d6f43-112">Yerel kanal tasarım kanal yığını hem hızını artırmak için seri hale getirme işlemi atlanıyor.</span><span class="sxs-lookup"><span data-stu-id="d6f43-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="d6f43-113">Yerel taşıma kanalının hizmet çağrıları istemciden hizmete taşımayı ve istemciye geri dönüş değeri için bir kuyruk kullanma uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d6f43-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="d6f43-114">Örnek parametreler ve dönüş değerleri serileştirme yerine, nesneleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="d6f43-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d6f43-115">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d6f43-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d6f43-116">Derleme ve LocalChannel çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d6f43-116">Build and run the LocalChannel solution.</span></span>  
  
2.  <span data-ttu-id="d6f43-117">Hizmet ana bilgisayarı başlatılır ve istemcinin yerel kanal'ı kullanarak hizmeti çağırır.</span><span class="sxs-lookup"><span data-stu-id="d6f43-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="d6f43-118">Hizmet arama sonuçlarını görüntülemek için bir konsol penceresi görünür.</span><span class="sxs-lookup"><span data-stu-id="d6f43-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d6f43-119">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="d6f43-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d6f43-120">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d6f43-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d6f43-121">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d6f43-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d6f43-122">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d6f43-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
