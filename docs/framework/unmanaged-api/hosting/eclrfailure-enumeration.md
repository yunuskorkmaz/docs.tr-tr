---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19dacae05766566521f563d0d24980c01dfb7a0b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144293"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="9e769-102">EClrFailure Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9e769-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="9e769-103">Bir ana bilgisayar ilkesi eylemleri ayarlayabilirsiniz hataları kümesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9e769-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e769-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e769-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="9e769-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9e769-105">Members</span></span>  
  
|<span data-ttu-id="9e769-106">Üye</span><span class="sxs-lookup"><span data-stu-id="9e769-106">Member</span></span>|<span data-ttu-id="9e769-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e769-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="9e769-108">Kod kritik olmayan bir bölgede (örneğin, bir iş parçacığı, bir bellek bloğu veya bir kilit) bir kaynağı ayırmak girişimi sırasında bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9e769-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="9e769-109">Kod kritik bir bölgede (örneğin, bir iş parçacığı, bir bellek bloğu veya bir kilit) bir kaynağı ayırmak girişimi sırasında bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9e769-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="9e769-110">Ortak dil çalışma zamanı (CLR) artık yönetilen kod işlemde çalışan mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="9e769-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="9e769-111">Henceforth, herhangi bir barındırma işlevleri çağrıları HOST_E_CLRNOTAVAILABLE bir HRESULT değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e769-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="9e769-112">Bir iş parçacığı döndürme bağlı bir kilidi serbest bırakmak başarısız bir <xref:System.AppDomain> nesne.</span><span class="sxs-lookup"><span data-stu-id="9e769-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="9e769-113">Konak bu hatanın neden iptal etmek için bir iş parçacığı ayarlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="9e769-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="9e769-114">Bir yığın taşması oluştu.</span><span class="sxs-lookup"><span data-stu-id="9e769-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="9e769-115">Okuma veya yazma korumalı bellek girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="9e769-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="9e769-116">Desteklenmez [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9e769-116">Not supported in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="9e769-117">Bir kod sözleşmesi hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9e769-117">A code contract failure occurred.</span></span> <span data-ttu-id="9e769-118">Bkz: [kod sözleşmeleri](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="9e769-118">See [Code Contracts](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e769-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e769-119">Remarks</span></span>  
 <span data-ttu-id="9e769-120">Bkz: [Iclrpolicymanager::setactiononfailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) yöntemi bir listesi için [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerleri konak hata koşulları için ilke eylemleri belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e769-120">See the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="9e769-121">Kod kritik ve kritik olmayan bölgeleri hakkında daha fazla bilgi için bkz. [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="9e769-121">For more information about critical and non-critical regions of code, see [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e769-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e769-122">Requirements</span></span>  
 <span data-ttu-id="9e769-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e769-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e769-124">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e769-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e769-125">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9e769-125">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9e769-126">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="9e769-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9e769-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e769-127">See also</span></span>

- [<span data-ttu-id="9e769-128">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e769-128">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="9e769-129">SetActionOnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e769-129">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="9e769-130">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e769-130">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="9e769-131">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="9e769-131">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
