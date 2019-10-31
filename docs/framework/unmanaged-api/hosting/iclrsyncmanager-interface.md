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
ms.openlocfilehash: 3593e4d68058a1820f575c92ff9571d43560316a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133928"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="6de17-102">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6de17-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="6de17-103">Konağın istenen görevler hakkında bilgi almasını ve eşitleme uygulamasında kilitlenmeleri algılamasını sağlayan yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6de17-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6de17-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6de17-104">Methods</span></span>  
  
|<span data-ttu-id="6de17-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6de17-105">Method</span></span>|<span data-ttu-id="6de17-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6de17-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6de17-107">CreateRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6de17-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="6de17-108">Ortak dil çalışma zamanının (CLR), bir okuyucu-yazıcı kilidinde bekleyen görev kümesini belirlemede kullanacağı konak için bir yineleyici oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="6de17-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="6de17-109">DeleteRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6de17-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="6de17-110">CLR 'nin `CreateRWLockOwnerIterator`çağrısı tarafından oluşturulan bir yineleyiciyi yok ettiğini ister.</span><span class="sxs-lookup"><span data-stu-id="6de17-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="6de17-111">GetMonitorOwner Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6de17-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="6de17-112">Belirtilen izleyicinin sahibi olan görevi alır.</span><span class="sxs-lookup"><span data-stu-id="6de17-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="6de17-113">GetRWLockOwnerNext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6de17-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="6de17-114">Geçerli okuyucu-yazıcı kilidinde bekleyen bir sonraki görevi alır.</span><span class="sxs-lookup"><span data-stu-id="6de17-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6de17-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6de17-115">Requirements</span></span>  
 <span data-ttu-id="6de17-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6de17-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6de17-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6de17-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6de17-118">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="6de17-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6de17-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6de17-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6de17-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6de17-120">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="6de17-121">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6de17-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <span data-ttu-id="6de17-122">[Yönetilen ve yönetilmeyen Iş parçacığı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6de17-122">[Managed and Unmanaged Threading](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>
- [<span data-ttu-id="6de17-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6de17-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
