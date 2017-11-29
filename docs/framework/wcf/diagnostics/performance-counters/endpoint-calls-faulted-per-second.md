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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4f52a0f0b44a788bd5c2d34c125e31884c2a9afb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-calls-faulted-per-second"></a><span data-ttu-id="20703-102">Uç Noktası: Saniyede Hatalı Çağrı</span><span class="sxs-lookup"><span data-stu-id="20703-102">Endpoint: Calls Faulted Per Second</span></span>
<span data-ttu-id="20703-103">Sayaç adı: Saniyede hatalı çağrı.</span><span class="sxs-lookup"><span data-stu-id="20703-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="20703-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20703-104">Description</span></span>  
 <span data-ttu-id="20703-105">Hataları Bu uç noktaya bir saniyede döndürmüş çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="20703-105">Number of calls that have returned faults to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="20703-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="20703-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="20703-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="20703-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="20703-108">İçinde [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] uygulamalar, hizmet yöntemleri iletişim SOAP hata iletileri kullanarak hata bilgilerini işleme.</span><span class="sxs-lookup"><span data-stu-id="20703-108">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="20703-109">SOAP, bir hizmet işlemi için meta verileri içinde yer alan ve bu nedenle istemcilerin kendi yürütme daha sağlam veya etkileşimli yapmak için kullanabileceği bir hataya sözleşmesi oluşturma ileti türlerini hatalarıdır.</span><span class="sxs-lookup"><span data-stu-id="20703-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="20703-110">XML formundaki istemcilere SOAP hataları ifade olduğundan, yüksek oranda birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="20703-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20703-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20703-111">See Also</span></span>  
 [<span data-ttu-id="20703-112">Belirtme ve sözleşme ve hizmetlerde hataları işleme</span><span class="sxs-lookup"><span data-stu-id="20703-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
