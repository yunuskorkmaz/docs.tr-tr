---
title: Saniyede Başarısız Olan Çağrı
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: 19f09b2a2132cab56da5dec49bdc8d5f5e4c8b8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474460"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="d4c73-102">Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="d4c73-102">Calls Failed Per Second</span></span>
<span data-ttu-id="d4c73-103">Sayaç adı: Saniyede başarısız olan çağrılar</span><span class="sxs-lookup"><span data-stu-id="d4c73-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="d4c73-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4c73-104">Description</span></span>  
 <span data-ttu-id="d4c73-105">Bu ikinci bir işlemde işlenmemiş özel durumlardan sahip çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="d4c73-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="d4c73-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="d4c73-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d4c73-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="d4c73-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="d4c73-108">Bu sayaç artırılır her, bu işlem içinde işlenmeyen bir özel yoktur.</span><span class="sxs-lookup"><span data-stu-id="d4c73-108">This counter is incremented everytime there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4c73-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4c73-109">See Also</span></span>  
 [<span data-ttu-id="d4c73-110">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="d4c73-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
