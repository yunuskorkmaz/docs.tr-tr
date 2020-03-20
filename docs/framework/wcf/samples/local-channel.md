---
title: Yerel Kanal
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 87e140395ac2fb5702d8655cf970da8a60c991ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144513"
---
# <a name="local-channel"></a><span data-ttu-id="f61df-102">Yerel Kanal</span><span class="sxs-lookup"><span data-stu-id="f61df-102">Local Channel</span></span>
<span data-ttu-id="f61df-103">Yerel Kanal, aynı uygulama etki alanı içinde iletişim için kullanılan bir Windows Communication Foundation (WCF) aktarım kanalıdır.</span><span class="sxs-lookup"><span data-stu-id="f61df-103">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="f61df-104">Bu, istemci ve hizmetin aynı uygulama etki alanında çalıştığı ve tipik WCF kanal yığınının (iletilerin serileştirme ve deserialization) ek yükünden kaçınılması gereken senaryolar için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f61df-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="f61df-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="f61df-105">Demonstrates</span></span>  
 <span data-ttu-id="f61df-106">Yerel Kanal</span><span class="sxs-lookup"><span data-stu-id="f61df-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="f61df-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="f61df-107">Discussion</span></span>  
 <span data-ttu-id="f61df-108">Örnek iki proje dosyasından oluşur:</span><span class="sxs-lookup"><span data-stu-id="f61df-108">The sample consists of two project files:</span></span>  
  
- <span data-ttu-id="f61df-109">**LocalChannel**: Yerel kanalın geçerli uygulama etki alanı içinde programlı gösterimi.</span><span class="sxs-lookup"><span data-stu-id="f61df-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="f61df-110">Bu projede, gönderen bileşen iletiyi bellek içi sıraya yerleştirir ve alıcı bileşen iletiyi almak için sırayı ayırır.</span><span class="sxs-lookup"><span data-stu-id="f61df-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
- <span data-ttu-id="f61df-111">**ClientAndService**: Bu proje bir konsol uygulamasında bir hizmeti barındırır ve ardından aynı uygulama etki alanı içinden hizmeti aramak için bir istemci çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="f61df-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="f61df-112">Yerel kanal tasarımı, hızı artırmak için hem kanal yığınını hem de serileştirme işlemini atlar.</span><span class="sxs-lookup"><span data-stu-id="f61df-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="f61df-113">Yerel aktarım kanalı, istemciden hizmet çağrılarını hizmete taşımak ve değeri istemciye geri döndürmek için bir sıra kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f61df-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="f61df-114">Örnek, parametreleri ve döndürme değerlerini serihale getirmek yerine nesneleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="f61df-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f61df-115">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f61df-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f61df-116">LocalChannel çözümlerini oluşturun ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f61df-116">Build and run the LocalChannel solution.</span></span>  
  
2. <span data-ttu-id="f61df-117">Hizmet ana bilgisayarı başlatılır ve istemci yerel kanalı kullanarak hizmeti çağırır.</span><span class="sxs-lookup"><span data-stu-id="f61df-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="f61df-118">Hizmet çağrısının sonuçlarını görüntülemek için bir konsol penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f61df-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f61df-119">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="f61df-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f61df-120">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f61df-120">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f61df-121">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="f61df-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f61df-122">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="f61df-122">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
