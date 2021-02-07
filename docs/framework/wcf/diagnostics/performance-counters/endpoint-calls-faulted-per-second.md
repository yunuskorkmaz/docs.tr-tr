---
description: 'Şu konuda daha fazla bilgi edinin: uç nokta: saniye başına hatalı çağrı'
title: 'Uç Noktası: Saniyede Hatalı Çağrı'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: 160680f215dbb3eea5ad15c756c7dc68a0629a90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759620"
---
# <a name="endpoint-calls-faulted-per-second"></a><span data-ttu-id="f0868-103">Uç Noktası: Saniyede Hatalı Çağrı</span><span class="sxs-lookup"><span data-stu-id="f0868-103">Endpoint: Calls Faulted Per Second</span></span>

<span data-ttu-id="f0868-104">Sayaç adı: saniye başına hatalı çağrı.</span><span class="sxs-lookup"><span data-stu-id="f0868-104">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f0868-105">Description</span><span class="sxs-lookup"><span data-stu-id="f0868-105">Description</span></span>  

 <span data-ttu-id="f0868-106">Bu uç noktaya saniye içinde hata döndüren çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="f0868-106">Number of calls that have returned faults to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="f0868-107">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="f0868-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="f0868-108">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="f0868-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="f0868-109">Windows Communication Foundation (WCF) uygulamalarında, hizmet yöntemleri SOAP hata iletilerini kullanarak işlem hata bilgilerini iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="f0868-109">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="f0868-110">SOAP hataları, bir hizmet işleminin meta verilerinde bulunan ileti türleridir ve bu nedenle, istemcilerinin yürütmesini daha sağlam veya etkileşimli hale getirmek için kullanabileceği bir hata sözleşmesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0868-110">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="f0868-111">SOAP hataları, XML biçiminde istemcilere belirtilediğinden, bunlar çok fazla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0868-111">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0868-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0868-112">See also</span></span>

- [<span data-ttu-id="f0868-113">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="f0868-113">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
