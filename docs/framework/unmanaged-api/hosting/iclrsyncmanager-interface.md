---
title: ICLRSyncManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
ms.openlocfilehash: b0b9c0b7d178557806a9ab2893bff2d34dc408ff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557742"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="ba597-102">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba597-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="ba597-103">Konağın istenen görevler hakkında bilgi almasını ve eşitleme uygulamasında kilitlenmeleri algılamasını sağlayan yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ba597-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ba597-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ba597-104">Methods</span></span>  
  
|<span data-ttu-id="ba597-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ba597-105">Method</span></span>|<span data-ttu-id="ba597-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba597-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ba597-107">CreateRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba597-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="ba597-108">Ortak dil çalışma zamanının (CLR), bir okuyucu-yazıcı kilidinde bekleyen görev kümesini belirlemede kullanacağı konak için bir yineleyici oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="ba597-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="ba597-109">DeleteRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba597-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="ba597-110">CLR 'nin bir çağrısıyla oluşturulmuş bir yineleyiciyi yok ettiğini ister `CreateRWLockOwnerIterator` .</span><span class="sxs-lookup"><span data-stu-id="ba597-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="ba597-111">GetMonitorOwner Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba597-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="ba597-112">Belirtilen izleyicinin sahibi olan görevi alır.</span><span class="sxs-lookup"><span data-stu-id="ba597-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="ba597-113">GetRWLockOwnerNext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba597-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="ba597-114">Geçerli okuyucu-yazıcı kilidinde bekleyen bir sonraki görevi alır.</span><span class="sxs-lookup"><span data-stu-id="ba597-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ba597-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba597-115">Requirements</span></span>  
 <span data-ttu-id="ba597-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba597-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba597-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ba597-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ba597-118">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ba597-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba597-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba597-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba597-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba597-120">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="ba597-121">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba597-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <span data-ttu-id="ba597-122">[Yönetilen ve yönetilmeyen Iş parçacığı](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ba597-122">[Managed and Unmanaged Threading](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>
- [<span data-ttu-id="ba597-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ba597-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
