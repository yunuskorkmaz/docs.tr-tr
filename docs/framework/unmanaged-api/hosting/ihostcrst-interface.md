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
ms.openlocfilehash: e8cb1486ccea11ba6edcf7bbb781a9bf210b496d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804909"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="e6dd4-102">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6dd4-102">IHostCrst Interface</span></span>
<span data-ttu-id="e6dd4-103">İş parçacığı için kritik bir bölümün ana bilgisayarın temsili olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="e6dd4-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e6dd4-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e6dd4-104">Methods</span></span>  
  
|<span data-ttu-id="e6dd4-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e6dd4-105">Method</span></span>|<span data-ttu-id="e6dd4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6dd4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e6dd4-107">Enter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6dd4-107">Enter Method</span></span>](ihostcrst-enter-method.md)|<span data-ttu-id="e6dd4-108">Kritik bölümüne girer.</span><span class="sxs-lookup"><span data-stu-id="e6dd4-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="e6dd4-109">Leave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6dd4-109">Leave Method</span></span>](ihostcrst-leave-method.md)|<span data-ttu-id="e6dd4-110">Kritik bölümünü bırakır.</span><span class="sxs-lookup"><span data-stu-id="e6dd4-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="e6dd4-111">SetSpinCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6dd4-111">SetSpinCount Method</span></span>](ihostcrst-setspincount-method.md)|<span data-ttu-id="e6dd4-112">Kritik bölüm için döngü sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e6dd4-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="e6dd4-113">TryEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6dd4-113">TryEnter Method</span></span>](ihostcrst-tryenter-method.md)|<span data-ttu-id="e6dd4-114">Kritik bölümü girmeye çalışır ve başarılı veya başarısız olarak anında rapor verebilir.</span><span class="sxs-lookup"><span data-stu-id="e6dd4-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6dd4-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6dd4-115">Remarks</span></span>  
 <span data-ttu-id="e6dd4-116">`IHostCrst`ortak dil çalışma zamanının (CLR), veya gibi Win32 işlevlerini kullanmak yerine, kritik bir bölümün temsili ile doğrudan iletişim kurmasına izin verir `EnterCriticalSection` `LeaveCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="e6dd4-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6dd4-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6dd4-117">Requirements</span></span>  
 <span data-ttu-id="e6dd4-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6dd4-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6dd4-119">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e6dd4-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e6dd4-120">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="e6dd4-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6dd4-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6dd4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6dd4-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6dd4-122">See also</span></span>

- [<span data-ttu-id="e6dd4-123">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6dd4-123">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="e6dd4-124">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6dd4-124">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="e6dd4-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e6dd4-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
