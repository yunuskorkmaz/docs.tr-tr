---
title: 'Uç Noktası: Saniyede Hatalı Çağrı'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: f1b2997a0f1e16c897fc319d1833313141f5c4bf
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44199602"
---
# <a name="endpoint-calls-faulted-per-second"></a><span data-ttu-id="9c1c5-102">Uç Noktası: Saniyede Hatalı Çağrı</span><span class="sxs-lookup"><span data-stu-id="9c1c5-102">Endpoint: Calls Faulted Per Second</span></span>
<span data-ttu-id="9c1c5-103">Sayaç adı: Saniyede hatalı çağrı.</span><span class="sxs-lookup"><span data-stu-id="9c1c5-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9c1c5-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c1c5-104">Description</span></span>  
 <span data-ttu-id="9c1c5-105">Bir saniye içinde döndürmüş hataları için bu endpoint çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="9c1c5-105">Number of calls that have returned faults to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="9c1c5-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="9c1c5-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="9c1c5-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="9c1c5-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="9c1c5-108">Windows Communication Foundation (WCF) uygulamaları, hizmet yöntemleri işleme hata bilgilerini SOAP hata iletileri kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="9c1c5-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="9c1c5-109">SOAP hatalarının bir hizmet işlemi için meta veriler bulunur ve bu nedenle istemcilerin yürütülmesi daha sağlam ve etkileşimli hale getirmek için kullanabileceği bir hataya sözleşmesi oluşturma iletisi türleridir.</span><span class="sxs-lookup"><span data-stu-id="9c1c5-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="9c1c5-110">SOAP hataları XML formundaki istemcilere ifade olduğundan, yüksek düzeyde birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="9c1c5-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c1c5-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9c1c5-111">See Also</span></span>  
 [<span data-ttu-id="9c1c5-112">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="9c1c5-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
