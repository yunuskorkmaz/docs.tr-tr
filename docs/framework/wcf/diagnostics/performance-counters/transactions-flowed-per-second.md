---
title: "Saniyede Akışı Yapılan İşlem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6769b3d875471ddb56b3888a49f72978f4ee786b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="4b1ee-102">Saniyede Akışı Yapılan İşlem</span><span class="sxs-lookup"><span data-stu-id="4b1ee-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="4b1ee-103">Sayaç adı: Saniye başına yapılan işlemler</span><span class="sxs-lookup"><span data-stu-id="4b1ee-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="4b1ee-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b1ee-104">Description</span></span>  
 <span data-ttu-id="4b1ee-105">Bu ikinci bir işlem için işlem sayısı aktarılan.</span><span class="sxs-lookup"><span data-stu-id="4b1ee-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="4b1ee-106">Bu sayaç, bir işlem kimliği işleme gönderilen bir ileti bulunur dilediğiniz zaman artırılır.</span><span class="sxs-lookup"><span data-stu-id="4b1ee-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="4b1ee-107">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="4b1ee-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="4b1ee-108">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="4b1ee-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
