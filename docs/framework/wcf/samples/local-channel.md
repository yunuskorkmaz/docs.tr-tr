---
title: Yerel Kanal
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 6bc1fac22f6eed3c9acb6b86f7611cbfb4e1d371
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714893"
---
# <a name="local-channel"></a><span data-ttu-id="bef4d-102">Yerel Kanal</span><span class="sxs-lookup"><span data-stu-id="bef4d-102">Local Channel</span></span>
<span data-ttu-id="bef4d-103">Yerel kanal, aynı uygulama etki alanı içinde iletişim için kullanılan bir Windows Communication Foundation (WCF) aktarım kanaldır.</span><span class="sxs-lookup"><span data-stu-id="bef4d-103">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="bef4d-104">Bu, istemcinin ve hizmetin aynı uygulama etki alanında çalıştığı senaryolarda ve tipik WCF kanal yığınının (iletilerin serileştirilmesi ve serisini kaldırma) önkullanılması kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bef4d-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="bef4d-105">Gösterir</span><span class="sxs-lookup"><span data-stu-id="bef4d-105">Demonstrates</span></span>  
 <span data-ttu-id="bef4d-106">Yerel Kanal</span><span class="sxs-lookup"><span data-stu-id="bef4d-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="bef4d-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="bef4d-107">Discussion</span></span>  
 <span data-ttu-id="bef4d-108">Örnek iki proje dosyasından oluşur:</span><span class="sxs-lookup"><span data-stu-id="bef4d-108">The sample consists of two project files:</span></span>  
  
- <span data-ttu-id="bef4d-109">**LocalChannel**: geçerli uygulama etki alanı içindeki yerel kanalın programlı gösterimi.</span><span class="sxs-lookup"><span data-stu-id="bef4d-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="bef4d-110">Bu projede, gönderme bileşeni iletiyi bellek içi kuyruğa koyar ve alıcı bileşen iletiyi alacak şekilde kuyruğa alır.</span><span class="sxs-lookup"><span data-stu-id="bef4d-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
- <span data-ttu-id="bef4d-111">**ClientAndService**: Bu proje bir konsol uygulamasında bir hizmet barındırır ve sonra aynı uygulama etki alanının içinden hizmeti çağırmak için bir istemci çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="bef4d-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="bef4d-112">Yerel kanal tasarımı, hızı artırmak için hem kanal yığınını hem de serileştirme işlemini atlar.</span><span class="sxs-lookup"><span data-stu-id="bef4d-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="bef4d-113">Yerel aktarım kanalı, hizmet çağrılarını istemciden hizmete aktarmak ve değeri istemciye geri döndürmek için bir kuyruk kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="bef4d-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="bef4d-114">Parametreleri ve dönüş değerlerini serileştirmek yerine, örnek nesneleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="bef4d-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bef4d-115">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="bef4d-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bef4d-116">LocalChannel çözümünü derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bef4d-116">Build and run the LocalChannel solution.</span></span>  
  
2. <span data-ttu-id="bef4d-117">Hizmet ana bilgisayarı başlatılır ve istemci yerel kanalı kullanarak hizmeti çağırır.</span><span class="sxs-lookup"><span data-stu-id="bef4d-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="bef4d-118">Hizmet çağrısının sonuçlarını görüntüleyen bir konsol penceresi görünür.</span><span class="sxs-lookup"><span data-stu-id="bef4d-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bef4d-119">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="bef4d-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bef4d-120">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bef4d-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="bef4d-121">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="bef4d-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bef4d-122">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="bef4d-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
