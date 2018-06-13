---
title: Saniyede Hatalı Çağrı
ms.date: 03/30/2017
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
ms.openlocfilehash: af84a379a36324131861aaa7e8577b5a44273917
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471347"
---
# <a name="calls-faulted-per-second"></a><span data-ttu-id="e2eb6-102">Saniyede Hatalı Çağrı</span><span class="sxs-lookup"><span data-stu-id="e2eb6-102">Calls Faulted Per Second</span></span>
<span data-ttu-id="e2eb6-103">Sayaç adı: Saniyede hatalı çağrı</span><span class="sxs-lookup"><span data-stu-id="e2eb6-103">Counter Name: Calls Faulted Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="e2eb6-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2eb6-104">Description</span></span>  
 <span data-ttu-id="e2eb6-105">Bu ikinci bir işlemde hataları döndürülen çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="e2eb6-105">Number of calls that returned faults to this operation in a second.</span></span>  
  
 <span data-ttu-id="e2eb6-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="e2eb6-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e2eb6-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="e2eb6-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="e2eb6-108">Windows Communication Foundation (WCF) uygulamalarında hizmet yöntemleri işleme hata bilgileri SOAP hata iletileri kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="e2eb6-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="e2eb6-109">SOAP, bir hizmet işlemi için meta verileri içinde yer alan ve bu nedenle istemcilerin kendi yürütme daha sağlam veya etkileşimli yapmak için kullanabileceği bir hataya sözleşmesi oluşturma ileti türlerini hatalarıdır.</span><span class="sxs-lookup"><span data-stu-id="e2eb6-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="e2eb6-110">XML formundaki istemcilere SOAP hataları ifade olduğundan, yüksek oranda birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="e2eb6-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2eb6-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2eb6-111">See Also</span></span>  
 [<span data-ttu-id="e2eb6-112">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="e2eb6-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
