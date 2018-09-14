---
title: Hata Verilen Güvenilir Mesajlaşma Oturumu/Saniye
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: c77d6a5f12dcce15dba94e2f63025a219ebcc6fd
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45514878"
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="55509-102">Hata Verilen Güvenilir Mesajlaşma Oturumu/Saniye</span><span class="sxs-lookup"><span data-stu-id="55509-102">Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="55509-103">Sayaç adı: Saniyede hatalı güvenilir Mesajlaşma oturumları.</span><span class="sxs-lookup"><span data-stu-id="55509-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="55509-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55509-104">Description</span></span>  
 <span data-ttu-id="55509-105">Bu hizmet, bir saniye içinde hatalı güvenilir Mesajlaşma oturumu sayısı.</span><span class="sxs-lookup"><span data-stu-id="55509-105">Number of reliable messaging sessions that are faulted in this service in a second.</span></span>  
  
 <span data-ttu-id="55509-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="55509-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="55509-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="55509-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
