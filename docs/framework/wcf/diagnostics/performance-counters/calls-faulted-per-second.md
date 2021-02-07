---
description: Hakkında daha fazla bilgi için bkz. saniyedeki hatalı çağrı
title: Saniyede Hatalı Çağrı
ms.date: 03/30/2017
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
ms.openlocfilehash: cbff7b24d2aa457bdbe3c600109f24c9672c7ab2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759685"
---
# <a name="calls-faulted-per-second"></a><span data-ttu-id="61bc4-103">Saniyede Hatalı Çağrı</span><span class="sxs-lookup"><span data-stu-id="61bc4-103">Calls Faulted Per Second</span></span>

<span data-ttu-id="61bc4-104">Sayaç adı: Hatalı çağrı/saniye</span><span class="sxs-lookup"><span data-stu-id="61bc4-104">Counter Name: Calls Faulted Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="61bc4-105">Description</span><span class="sxs-lookup"><span data-stu-id="61bc4-105">Description</span></span>  

 <span data-ttu-id="61bc4-106">Saniye içinde bu işleme hata döndüren çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="61bc4-106">Number of calls that returned faults to this operation in a second.</span></span>  
  
 <span data-ttu-id="61bc4-107">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="61bc4-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="61bc4-108">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="61bc4-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="61bc4-109">Windows Communication Foundation (WCF) uygulamalarında, hizmet yöntemleri SOAP hata iletilerini kullanarak işlem hata bilgilerini iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="61bc4-109">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="61bc4-110">SOAP hataları, bir hizmet işleminin meta verilerinde bulunan ileti türleridir ve bu nedenle, istemcilerinin yürütmesini daha sağlam veya etkileşimli hale getirmek için kullanabileceği bir hata sözleşmesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="61bc4-110">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="61bc4-111">SOAP hataları, XML biçiminde istemcilere belirtilediğinden, bunlar çok fazla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="61bc4-111">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61bc4-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61bc4-112">See also</span></span>

- [<span data-ttu-id="61bc4-113">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="61bc4-113">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
