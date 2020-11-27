---
title: 'Hizmet: Saniyede Başarısız Olan Çağrı'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: c97e4b0c6c2c71756a9bed7b1a2359ad0c118a98
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252978"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="5fea6-102">Hizmet: Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="5fea6-102">Service: Calls Failed Per Second</span></span>

<span data-ttu-id="5fea6-103">Sayaç adı: saniye başına başarısız çağrı.</span><span class="sxs-lookup"><span data-stu-id="5fea6-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5fea6-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fea6-104">Description</span></span>  

 <span data-ttu-id="5fea6-105">İşlenmemiş özel durumlara sahip ve bu hizmet tarafından bir saniyede alınan çağrıların sayısı.</span><span class="sxs-lookup"><span data-stu-id="5fea6-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="5fea6-106">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="5fea6-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5fea6-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="5fea6-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="5fea6-108">Yönetilen kodda, hata koşulları oluştuğunda özel durumlar oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5fea6-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="5fea6-109">Yönetilen kodda, hata koşulları oluştuğunda özel durumlar oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5fea6-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="5fea6-110">Bu hizmette işlenmeyen bir özel durum olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="5fea6-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fea6-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fea6-111">See also</span></span>

- [<span data-ttu-id="5fea6-112">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="5fea6-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
