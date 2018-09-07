---
title: Saniyede Bırakılan Güvenli Mesajlaşma İletileri
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 7722b32f99b302c5c272e095033879c9e04c7ee1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075390"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="f64ca-102">Saniyede Bırakılan Güvenli Mesajlaşma İletileri</span><span class="sxs-lookup"><span data-stu-id="f64ca-102">Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="f64ca-103">Sayaç adı: Saniye başına bırakılan güvenilir Mesajlaşma oturumları.</span><span class="sxs-lookup"><span data-stu-id="f64ca-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f64ca-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f64ca-104">Description</span></span>  
 <span data-ttu-id="f64ca-105">Bu hizmet, bir saniye içinde bırakılmış olan güvenilir Mesajlaşma iletileri toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="f64ca-105">Total number of reliable messaging messages that have been dropped in this service in a second.</span></span>  
  
 <span data-ttu-id="f64ca-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="f64ca-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="f64ca-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="f64ca-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
