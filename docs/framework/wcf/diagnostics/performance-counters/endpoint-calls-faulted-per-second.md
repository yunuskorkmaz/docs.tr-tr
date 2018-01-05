---
title: "Uç Noktası: Saniyede Hatalı Çağrı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 842270d6e570767c25c414307be941f24b01dd07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-calls-faulted-per-second"></a><span data-ttu-id="fceb8-102">Uç Noktası: Saniyede Hatalı Çağrı</span><span class="sxs-lookup"><span data-stu-id="fceb8-102">Endpoint: Calls Faulted Per Second</span></span>
<span data-ttu-id="fceb8-103">Sayaç adı: Saniyede hatalı çağrı.</span><span class="sxs-lookup"><span data-stu-id="fceb8-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fceb8-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fceb8-104">Description</span></span>  
 <span data-ttu-id="fceb8-105">Hataları Bu uç noktaya bir saniyede döndürmüş çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="fceb8-105">Number of calls that have returned faults to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="fceb8-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="fceb8-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="fceb8-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="fceb8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="fceb8-108">İçinde [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] uygulamalar, hizmet yöntemleri iletişim SOAP hata iletileri kullanarak hata bilgilerini işleme.</span><span class="sxs-lookup"><span data-stu-id="fceb8-108">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="fceb8-109">SOAP, bir hizmet işlemi için meta verileri içinde yer alan ve bu nedenle istemcilerin kendi yürütme daha sağlam veya etkileşimli yapmak için kullanabileceği bir hataya sözleşmesi oluşturma ileti türlerini hatalarıdır.</span><span class="sxs-lookup"><span data-stu-id="fceb8-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="fceb8-110">XML formundaki istemcilere SOAP hataları ifade olduğundan, yüksek oranda birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="fceb8-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fceb8-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fceb8-111">See Also</span></span>  
 [<span data-ttu-id="fceb8-112">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="fceb8-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
