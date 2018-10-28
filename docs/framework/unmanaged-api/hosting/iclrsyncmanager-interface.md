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
ms.openlocfilehash: ede896cdb93217fcfba9d66ed7102bcc1ba762e9
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50041836"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="14146-102">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14146-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="14146-103">İstenilen görevler hakkında bilgi almak ve kilitlenmeleri eşitleme uygulanması algılamak için konak izin verme yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="14146-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="14146-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="14146-104">Methods</span></span>  
  
|<span data-ttu-id="14146-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="14146-105">Method</span></span>|<span data-ttu-id="14146-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14146-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="14146-107">CreateRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14146-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="14146-108">Ortak dil çalışma zamanı (CLR) Okuyucu-Yazıcı kilit Bekleyen görevler kümesini belirlemek için kullanılacak ana bilgisayar için bir yineleyici oluşturma isteği.</span><span class="sxs-lookup"><span data-stu-id="14146-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="14146-109">DeleteRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14146-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="14146-110">CLR bir çağrı tarafından oluşturulan bir yineleyici yok istekleri `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="14146-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="14146-111">GetMonitorOwner Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14146-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="14146-112">Belirtilen İzleyici sahip görev alır.</span><span class="sxs-lookup"><span data-stu-id="14146-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="14146-113">GetRWLockOwnerNext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14146-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="14146-114">Geçerli Okuyucu-Yazıcı kilidi beklerken sonraki görev alır.</span><span class="sxs-lookup"><span data-stu-id="14146-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14146-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14146-115">Requirements</span></span>  
 <span data-ttu-id="14146-116">**Platformlar:** bkz [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14146-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14146-117">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="14146-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="14146-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="14146-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14146-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14146-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14146-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="14146-120">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="14146-121">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14146-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="14146-122">[Yönetilen ve yönetilmeyen iş parçacığı oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="14146-122">[Managed and Unmanaged Threading](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>  
 [<span data-ttu-id="14146-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="14146-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
