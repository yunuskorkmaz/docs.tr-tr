---
title: Uygulanıp Durdurulan İşlem/Saniye
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: 6369fea6def5ebb6b62274caed31d5fb63b3b0e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998198"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="34c74-102">Uygulanıp Durdurulan İşlem/Saniye</span><span class="sxs-lookup"><span data-stu-id="34c74-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="34c74-103">Sayaç adı: Saniye başına durdurulan işlemler.</span><span class="sxs-lookup"><span data-stu-id="34c74-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="34c74-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34c74-104">Description</span></span>  
 <span data-ttu-id="34c74-105">Bir saniye içinde bu hizmet durdurulmuş işlem alt işlemlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="34c74-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="34c74-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="34c74-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="34c74-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="34c74-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
