---
title: EMemoryCriticalLevel Numaralandırması
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ee8705d00e1f63f69863d0bf8e7d0d9d62807e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968616"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="0d038-102">EMemoryCriticalLevel Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0d038-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="0d038-103">Belirli bir bellek ayırma istendi ancak memnun olamaz, bir hatanın etkisini gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0d038-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d038-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d038-104">Syntax</span></span>  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="0d038-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0d038-105">Members</span></span>  
  
|<span data-ttu-id="0d038-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0d038-106">Member</span></span>|<span data-ttu-id="0d038-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d038-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="0d038-108">Ayırma ayırma istedi etki alanındaki yönetilen kodu yürütmek için kritik olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d038-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="0d038-109">Bellek tahsis edilemiyor, CLR etki alanı hala kullanılabilir olduğunu garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="0d038-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="0d038-110">Konak ayırma getirdiğinizde hangi eylemin karar verir.</span><span class="sxs-lookup"><span data-stu-id="0d038-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="0d038-111">CLR'nin iptal edilmemelerini sağlayabilirsiniz `AppDomain` otomatik olarak ya da üzerinde yöntemleri çağırarak çalıştırmaya devam etmesine izin [Iclrpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0d038-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="0d038-112">Ayırma işleminde yönetilen kodun yürütülmesi için önemli olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d038-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="0d038-113">Bu değer, başlatılırken ve sonlandırıcılar çalıştırırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0d038-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="0d038-114">Bellek tahsis edilemiyor, CLR'nin işlemdeki çalışamaz.</span><span class="sxs-lookup"><span data-stu-id="0d038-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="0d038-115">Ayırma başarısız olursa, CLR etkili bir şekilde devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="0d038-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="0d038-116">CLR hata HOST_E_CLRNOTAVAILABLE ile tüm sonraki çağırıyor.</span><span class="sxs-lookup"><span data-stu-id="0d038-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="0d038-117">Ayırma ayırma istediği görevi çalıştırmak için önemli olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d038-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="0d038-118">Bellek tahsis edilemiyor, CLR görev yürütülebilecek garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="0d038-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="0d038-119">CLR hata durumunda başlatır bir <xref:System.Threading.ThreadAbortException> fiziksel işlemi sistemi iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="0d038-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d038-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d038-120">Remarks</span></span>  
 <span data-ttu-id="0d038-121">Tanımlanan bellek ayırma yöntemleri [Ihostmemorymanager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) ve [Ihostmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) arabirimler bu türde bir parametre yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="0d038-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="0d038-122">Bir hata önem derecesi bağlı olarak, bir konak ayırma istek hemen başarısız mı, yoksa, karşılanamayacak kadar beklenecek karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d038-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d038-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d038-123">Requirements</span></span>  
 <span data-ttu-id="0d038-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d038-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d038-125">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0d038-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d038-126">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d038-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d038-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d038-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d038-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d038-128">See also</span></span>

- [<span data-ttu-id="0d038-129">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d038-129">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="0d038-130">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="0d038-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
