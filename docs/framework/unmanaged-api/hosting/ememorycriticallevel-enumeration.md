---
description: 'Daha fazla bilgi edinin: Ememorykritiklevel numaralandırması'
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
ms.openlocfilehash: 88965a29164de1ec7b01c2fcc8f51415127e69fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785438"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="0d5ec-103">EMemoryCriticalLevel Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0d5ec-103">EMemoryCriticalLevel Enumeration</span></span>

<span data-ttu-id="0d5ec-104">Belirli bir bellek ayırma talep edildiğinde, ancak karşılanamaması durumunda hatanın etkisini gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0d5ec-104">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d5ec-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0d5ec-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="0d5ec-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0d5ec-106">Members</span></span>  
  
|<span data-ttu-id="0d5ec-107">Üye</span><span class="sxs-lookup"><span data-stu-id="0d5ec-107">Member</span></span>|<span data-ttu-id="0d5ec-108">Description</span><span class="sxs-lookup"><span data-stu-id="0d5ec-108">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="0d5ec-109">Ayırmayı isteyen etki alanında yönetilen kodu yürütmek için ayırmanın kritik olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d5ec-109">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="0d5ec-110">Bellek ayrılabileceği takdirde, CLR etki alanının hala kullanılabilir olduğundan emin olamaz.</span><span class="sxs-lookup"><span data-stu-id="0d5ec-110">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="0d5ec-111">Ana bilgisayar, ayırma karşılanmıyorsa hangi eylemin yapılacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="0d5ec-111">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="0d5ec-112">CLR 'nin `AppDomain` otomatik olarak iptal etmesini veya [ICLRPolicyManager](iclrpolicymanager-interface.md)'daki yöntemleri çağırarak çalışmaya devam etmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d5ec-112">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="0d5ec-113">Ayırmanın, işlemdeki yönetilen kodun yürütülmesi için kritik öneme sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d5ec-113">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="0d5ec-114">Bu değer başlangıç sırasında ve sonlandırıcılar çalıştırılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0d5ec-114">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="0d5ec-115">Bellek ayrılabileceği takdirde, CLR işlemde çalışamaz.</span><span class="sxs-lookup"><span data-stu-id="0d5ec-115">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="0d5ec-116">Ayırma başarısız olursa, CLR etkin bir şekilde devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="0d5ec-116">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="0d5ec-117">CLR 'ye yapılan tüm sonraki çağrılar HOST_E_CLRNOTAVAILABLE ile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0d5ec-117">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="0d5ec-118">Ayırmayı isteyen görevi çalıştırmak için ayırmanın kritik olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d5ec-118">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="0d5ec-119">Bellek ayrılabileceği takdirde, CLR görevin yürütülüp yürütülabileceğini garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="0d5ec-119">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="0d5ec-120">Hata durumunda, CLR <xref:System.Threading.ThreadAbortException> fiziksel işlem sistemi iş parçacığı üzerinde bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0d5ec-120">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d5ec-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d5ec-121">Remarks</span></span>  

 <span data-ttu-id="0d5ec-122">[IHostMemoryManager](ihostmemorymanager-interface.md) ve [IHostMAlloc](ihostmalloc-interface.md) arabirimlerinde tanımlanan bellek ayırma yöntemleri bu türden bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="0d5ec-122">The memory allocation methods defined in the [IHostMemoryManager](ihostmemorymanager-interface.md) and [IHostMAlloc](ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="0d5ec-123">Bir hata önem derecesine bağlı olarak, bir ana bilgisayar, ayırma isteğinin hemen başarısız olmasına veya karşılanmayacağı kadar bekleyip bekmeyeceğine karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="0d5ec-123">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d5ec-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d5ec-124">Requirements</span></span>  

 <span data-ttu-id="0d5ec-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d5ec-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d5ec-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0d5ec-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d5ec-127">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d5ec-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d5ec-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d5ec-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d5ec-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d5ec-129">See also</span></span>

- [<span data-ttu-id="0d5ec-130">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d5ec-130">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="0d5ec-131">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="0d5ec-131">Hosting Enumerations</span></span>](hosting-enumerations.md)
