---
description: 'Daha fazla bilgi edinin: EClrFailure numaralandırması'
title: EClrFailure Numaralandırması
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
ms.openlocfilehash: 9f3a2270651e5b05d2d31ed90511b8eb05dd4d44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785594"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="3d27b-103">EClrFailure Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3d27b-103">EClrFailure Enumeration</span></span>

<span data-ttu-id="3d27b-104">Bir konağın ilke eylemlerini ayarlayabileceği başarısızlık kümesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="3d27b-104">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d27b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3d27b-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a><span data-ttu-id="3d27b-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3d27b-106">Members</span></span>  
  
|<span data-ttu-id="3d27b-107">Üye</span><span class="sxs-lookup"><span data-stu-id="3d27b-107">Member</span></span>|<span data-ttu-id="3d27b-108">Description</span><span class="sxs-lookup"><span data-stu-id="3d27b-108">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="3d27b-109">Kritik olmayan bir kod bölgesinde bir kaynak (iş parçacığı, bir bellek bloğu veya kilit gibi) ayırma girişimi sırasında bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3d27b-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="3d27b-110">Kritik kod bölgesinde bir kaynak (iş parçacığı, bir bellek bloğu veya kilit gibi) ayırma girişimi sırasında bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3d27b-110">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="3d27b-111">Ortak dil çalışma zamanı (CLR), işlemde yönetilen kodu artık çalıştıraamayacak.</span><span class="sxs-lookup"><span data-stu-id="3d27b-111">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="3d27b-112">Henceileri, herhangi bir barındırma işlevlerine yapılan çağrılar HOST_E_CLRNOTAVAILABLE HRESULT değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3d27b-112">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="3d27b-113">Bir iş parçacığı bir nesneden dönmeden bir kilidi serbest bırakmaya başarısız oldu <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="3d27b-113">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="3d27b-114">Konak, bir iş parçacığının iptal edilmesini sağlamak için bu hatayı ayarlayamadı.</span><span class="sxs-lookup"><span data-stu-id="3d27b-114">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="3d27b-115">Yığın taşması oluştu.</span><span class="sxs-lookup"><span data-stu-id="3d27b-115">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="3d27b-116">Korunan bellek okuma veya yazma girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="3d27b-116">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="3d27b-117">.NET Framework 4 ' te desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="3d27b-117">Not supported in the .NET Framework 4.</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="3d27b-118">Bir kod sözleşmesi hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="3d27b-118">A code contract failure occurred.</span></span> <span data-ttu-id="3d27b-119">Bkz. [Kod sözleşmeleri](../../debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="3d27b-119">See [Code Contracts](../../debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d27b-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d27b-120">Remarks</span></span>  

 <span data-ttu-id="3d27b-121">Konağın hata koşulları için ilke eylemlerini belirtmek için kullanabileceği [EPolicyAction](epolicyaction-enumeration.md) değerlerinin bir listesi Için [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) yöntemine bakın.</span><span class="sxs-lookup"><span data-stu-id="3d27b-121">See the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="3d27b-122">Kritik ve kritik olmayan kod bölgeleri hakkında daha fazla bilgi için bkz. [EClrOperation](eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="3d27b-122">For more information about critical and non-critical regions of code, see [EClrOperation](eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d27b-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d27b-123">Requirements</span></span>  

 <span data-ttu-id="3d27b-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d27b-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d27b-125">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3d27b-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d27b-126">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3d27b-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d27b-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d27b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d27b-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d27b-128">See also</span></span>

- [<span data-ttu-id="3d27b-129">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d27b-129">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="3d27b-130">SetActionOnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d27b-130">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="3d27b-131">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d27b-131">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="3d27b-132">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="3d27b-132">Hosting Enumerations</span></span>](hosting-enumerations.md)
