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
ms.openlocfilehash: d3e4affa363083ce55ac3764c26412a0d60ba3f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203099"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="40ba8-102">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40ba8-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="40ba8-103">İstenilen görevler hakkında bilgi almak ve kilitlenmeleri eşitleme uygulanması algılamak için konak izin verme yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="40ba8-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40ba8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="40ba8-104">Methods</span></span>  
  
|<span data-ttu-id="40ba8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="40ba8-105">Method</span></span>|<span data-ttu-id="40ba8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40ba8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40ba8-107">CreateRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40ba8-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="40ba8-108">Ortak dil çalışma zamanı (CLR) Okuyucu-Yazıcı kilit Bekleyen görevler kümesini belirlemek için kullanılacak ana bilgisayar için bir yineleyici oluşturma isteği.</span><span class="sxs-lookup"><span data-stu-id="40ba8-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="40ba8-109">DeleteRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40ba8-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="40ba8-110">CLR bir çağrı tarafından oluşturulan bir yineleyici yok istekleri `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="40ba8-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="40ba8-111">GetMonitorOwner Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40ba8-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="40ba8-112">Belirtilen İzleyici sahip görev alır.</span><span class="sxs-lookup"><span data-stu-id="40ba8-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="40ba8-113">GetRWLockOwnerNext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40ba8-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="40ba8-114">Geçerli Okuyucu-Yazıcı kilidi beklerken sonraki görev alır.</span><span class="sxs-lookup"><span data-stu-id="40ba8-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40ba8-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40ba8-115">Requirements</span></span>  
 <span data-ttu-id="40ba8-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40ba8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40ba8-117">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="40ba8-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40ba8-118">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="40ba8-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="40ba8-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="40ba8-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="40ba8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40ba8-120">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="40ba8-121">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40ba8-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="40ba8-122">Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="40ba8-122">Managed and Unmanaged Threading</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [<span data-ttu-id="40ba8-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="40ba8-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
