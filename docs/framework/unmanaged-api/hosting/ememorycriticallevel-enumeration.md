---
title: "EMemoryCriticalLevel Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryCriticalLevel
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryCriticalLevel
helpviewer_keywords: EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b15a6786cb99a64d441d7e05fb91cd8ff0f3af92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="07361-102">EMemoryCriticalLevel Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="07361-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="07361-103">Bir hata etkisi belirli bellek ayırma istendi ancak memnun olamaz belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="07361-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07361-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07361-104">Syntax</span></span>  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="07361-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="07361-105">Members</span></span>  
  
|<span data-ttu-id="07361-106">Üye</span><span class="sxs-lookup"><span data-stu-id="07361-106">Member</span></span>|<span data-ttu-id="07361-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07361-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="07361-108">Ayırma ayırma istedi etki alanında yönetilen kod yürütmek için önemli olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="07361-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="07361-109">Bellek ayrılamıyor, CLR etki alanı hala kullanılabilir garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="07361-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="07361-110">Konak ayırma karşılanamayan olduğunda gerçekleştirilecek eylemi karar verir.</span><span class="sxs-lookup"><span data-stu-id="07361-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="07361-111">İptal etmek için CLR söyleyebilirsiniz `AppDomain` otomatik olarak veya üzerinde yöntemler çağrılarak çalıştırmaya devam etmesine izin [Iclrpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="07361-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="07361-112">Ayırma işleminde yönetilen kod yürütülmesi için önemli olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="07361-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="07361-113">Bu değer, başlatma sırasında ve sonlandırıcılar çalıştırılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="07361-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="07361-114">Bellek ayrılamıyor, CLR işleminde çalışamaz.</span><span class="sxs-lookup"><span data-stu-id="07361-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="07361-115">Ayırma başarısız olursa, CLR etkili bir şekilde devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="07361-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="07361-116">CLR tüm sonraki çağrılar ile HOST_E_CLRNOTAVAILABLE başarısız.</span><span class="sxs-lookup"><span data-stu-id="07361-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="07361-117">Ayırma ayırma istedi görevi çalıştırmak için önemli olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="07361-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="07361-118">Bellek ayrılamıyor, CLR görev yürütülen garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="07361-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="07361-119">CLR hatası durumunda başlatır bir <xref:System.Threading.ThreadAbortException> fiziksel işlemi sistem iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="07361-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07361-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07361-120">Remarks</span></span>  
 <span data-ttu-id="07361-121">Tanımlanan bellek ayırma yöntemlerini [Ihostmemorymanager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) ve [Ihostmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) arabirimler bu türde bir parametre yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="07361-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="07361-122">Bir hata önem derecesi bağlı olarak, bir konak ayırma isteği hemen başarısız mı, yoksa, karşılanabilir kadar beklemeniz karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07361-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07361-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07361-123">Requirements</span></span>  
 <span data-ttu-id="07361-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07361-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07361-125">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="07361-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="07361-126">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="07361-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07361-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07361-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07361-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07361-128">See Also</span></span>  
 [<span data-ttu-id="07361-129">Iclrmemorynotificationcallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="07361-129">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [<span data-ttu-id="07361-130">Barındırma numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="07361-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
