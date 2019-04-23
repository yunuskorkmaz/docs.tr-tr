---
title: Saniyede Hatalı Çağrı
ms.date: 03/30/2017
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
ms.openlocfilehash: 5b7569b6a00757fbb863b90b25b44815a349ab07
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115524"
---
# <a name="calls-faulted-per-second"></a><span data-ttu-id="dacf2-102">Saniyede Hatalı Çağrı</span><span class="sxs-lookup"><span data-stu-id="dacf2-102">Calls Faulted Per Second</span></span>
<span data-ttu-id="dacf2-103">Sayaç adı: Saniyede Hatalı Çağrı</span><span class="sxs-lookup"><span data-stu-id="dacf2-103">Counter Name: Calls Faulted Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="dacf2-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dacf2-104">Description</span></span>  
 <span data-ttu-id="dacf2-105">Döndürmüş bu işleme bir saniye içinde çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="dacf2-105">Number of calls that returned faults to this operation in a second.</span></span>  
  
 <span data-ttu-id="dacf2-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="dacf2-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="dacf2-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="dacf2-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="dacf2-108">Windows Communication Foundation (WCF) uygulamaları, hizmet yöntemleri işleme hata bilgilerini SOAP hata iletileri kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="dacf2-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="dacf2-109">SOAP hatalarının bir hizmet işlemi için meta veriler bulunur ve bu nedenle istemcilerin yürütülmesi daha sağlam ve etkileşimli hale getirmek için kullanabileceği bir hataya sözleşmesi oluşturma iletisi türleridir.</span><span class="sxs-lookup"><span data-stu-id="dacf2-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="dacf2-110">SOAP hataları XML formundaki istemcilere ifade olduğundan, yüksek düzeyde birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="dacf2-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dacf2-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dacf2-111">See also</span></span>

- [<span data-ttu-id="dacf2-112">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="dacf2-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
