---
title: "Saniyede Başarısız Olan Çağrı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 504470a7338a22d058f6ae1f99192e9665b4d968
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="7f553-102">Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="7f553-102">Calls Failed Per Second</span></span>
<span data-ttu-id="7f553-103">Sayaç adı: Saniyede başarısız olan çağrılar</span><span class="sxs-lookup"><span data-stu-id="7f553-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="7f553-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f553-104">Description</span></span>  
 <span data-ttu-id="7f553-105">Bu ikinci bir işlemde işlenmemiş özel durumlardan sahip çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="7f553-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="7f553-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="7f553-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="7f553-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="7f553-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="7f553-108">Bu sayaç artırılır her, bu işlem içinde işlenmeyen bir özel yoktur.</span><span class="sxs-lookup"><span data-stu-id="7f553-108">This counter is incremented everytime there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f553-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7f553-109">See Also</span></span>  
 [<span data-ttu-id="7f553-110">Belirtme ve sözleşme ve hizmetlerde hataları işleme</span><span class="sxs-lookup"><span data-stu-id="7f553-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
