---
title: "Saniyede Bırakılan Güvenli Mesajlaşma İletileri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dbae9414c4ce5394fc0d4a83589e2e5e10ffcc8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="a1847-102">Saniyede Bırakılan Güvenli Mesajlaşma İletileri</span><span class="sxs-lookup"><span data-stu-id="a1847-102">Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="a1847-103">Sayaç adı: Saniye başına bırakılan güvenilir Mesajlaşma oturumları.</span><span class="sxs-lookup"><span data-stu-id="a1847-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a1847-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1847-104">Description</span></span>  
 <span data-ttu-id="a1847-105">Bu hizmet bir saniyede bırakılan güvenli Mesajlaşma iletileri toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="a1847-105">Total number of reliable messaging messages that have been dropped in this service in a second.</span></span>  
  
 <span data-ttu-id="a1847-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="a1847-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="a1847-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="a1847-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
