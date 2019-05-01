---
title: 'Hizmet: Saniyede Hatalı Çağrı'
ms.date: 03/30/2017
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
ms.openlocfilehash: 595b623d70bad82ea39ab3ef93fb5fd499268ff2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61915713"
---
# <a name="service-calls-faulted-per-second"></a><span data-ttu-id="5fe8e-102">Hizmet: Saniyede Hatalı Çağrı</span><span class="sxs-lookup"><span data-stu-id="5fe8e-102">Service: Calls Faulted Per Second</span></span>
<span data-ttu-id="5fe8e-103">Sayaç adı: Saniyede hatalı çağrı.</span><span class="sxs-lookup"><span data-stu-id="5fe8e-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5fe8e-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fe8e-104">Description</span></span>  
 <span data-ttu-id="5fe8e-105">Hataları bir saniye içinde bu hizmete iade çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="5fe8e-105">Number of calls that have returned faults to this service in a second.</span></span>  
  
 <span data-ttu-id="5fe8e-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="5fe8e-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5fe8e-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="5fe8e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="5fe8e-108">Windows Communication Foundation (WCF) uygulamaları, hizmet yöntemleri işleme hata bilgilerini SOAP hata iletileri kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="5fe8e-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="5fe8e-109">SOAP hatalarının bir hizmet işlemi için meta veriler bulunur ve bu nedenle istemcilerin yürütülmesi daha sağlam ve etkileşimli hale getirmek için kullanabileceği bir hataya sözleşmesi oluşturma iletisi türleridir.</span><span class="sxs-lookup"><span data-stu-id="5fe8e-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="5fe8e-110">SOAP hataları XML formundaki istemcilere ifade olduğundan, yüksek düzeyde birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="5fe8e-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fe8e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fe8e-111">See also</span></span>

- [<span data-ttu-id="5fe8e-112">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="5fe8e-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
