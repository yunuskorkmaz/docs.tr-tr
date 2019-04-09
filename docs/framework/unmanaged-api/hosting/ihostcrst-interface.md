---
title: IHostCrst Arabirimi
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 939f100e8ee386642a29c33827a8339caf0467b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193193"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="d3041-102">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3041-102">IHostCrst Interface</span></span>
<span data-ttu-id="d3041-103">İş parçacığı için kritik bir bölüm konağın gösterimi işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="d3041-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3041-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d3041-104">Methods</span></span>  
  
|<span data-ttu-id="d3041-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d3041-105">Method</span></span>|<span data-ttu-id="d3041-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3041-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3041-107">Enter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3041-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="d3041-108">Kritik bölüm girer.</span><span class="sxs-lookup"><span data-stu-id="d3041-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="d3041-109">Leave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3041-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="d3041-110">Kritik bölüm bırakır.</span><span class="sxs-lookup"><span data-stu-id="d3041-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="d3041-111">SetSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3041-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="d3041-112">Kritik bölüm için dönüş sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d3041-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="d3041-113">TryEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3041-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="d3041-114">Kritik bölüm ve raporları başarı veya başarısızlık hemen girmek çalışır.</span><span class="sxs-lookup"><span data-stu-id="d3041-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3041-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3041-115">Remarks</span></span>  
 `IHostCrst` <span data-ttu-id="d3041-116">Ortak dil çalışma zamanı (CLR) kritik bir bölüm doğrudan ana bilgisayarın gösterimi ile iletişim kurmak için Win32 işlevlerini gibi kullanmak yerine sağlayan `EnterCriticalSection` veya `LeaveCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="d3041-116">allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3041-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3041-117">Requirements</span></span>  
 <span data-ttu-id="d3041-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3041-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3041-119">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d3041-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3041-120">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d3041-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="d3041-121">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d3041-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d3041-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3041-122">See also</span></span>

- [<span data-ttu-id="d3041-123">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3041-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="d3041-124">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3041-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="d3041-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d3041-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
