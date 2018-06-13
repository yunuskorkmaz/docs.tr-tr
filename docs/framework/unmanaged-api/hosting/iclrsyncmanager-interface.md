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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b87ccc3d6c3e957d0384499048032e35247093a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436487"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="733be-102">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="733be-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="733be-103">İstenen görevler hakkında bilgi almak ve kendi eşitleme uygulamasında kilitlenmeleri algılamak için konak izin yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="733be-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="733be-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="733be-104">Methods</span></span>  
  
|<span data-ttu-id="733be-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="733be-105">Method</span></span>|<span data-ttu-id="733be-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="733be-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="733be-107">CreateRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="733be-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="733be-108">Ortak dil çalışma zamanı (CLR) oluşturma yineleyici Okuyucu-Yazıcı kilit Bekleyen Görevler belirlemek için kullanılacak ana bilgisayar için istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="733be-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="733be-109">DeleteRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="733be-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="733be-110">CLR yapılan bir çağrı tarafından oluşturulan bir yineleyici destroy istekleri `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="733be-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="733be-111">GetMonitorOwner Yöntemi</span><span class="sxs-lookup"><span data-stu-id="733be-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="733be-112">Belirtilen İzleyici sahibi görev alır.</span><span class="sxs-lookup"><span data-stu-id="733be-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="733be-113">GetRWLockOwnerNext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="733be-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="733be-114">Geçerli Okuyucu-Yazıcı kilidi beklerken sonraki görev alır.</span><span class="sxs-lookup"><span data-stu-id="733be-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="733be-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="733be-115">Requirements</span></span>  
 <span data-ttu-id="733be-116">**Platformlar:** bkz [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="733be-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="733be-117">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="733be-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="733be-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="733be-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="733be-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="733be-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="733be-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="733be-120">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="733be-121">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="733be-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="733be-122">[Yönetilen ve yönetilmeyen iş parçacığı oluşturma](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="733be-122">[Managed and Unmanaged Threading](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))</span></span>  
 [<span data-ttu-id="733be-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="733be-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
