---
title: "IHostMemoryManager::AcquiredVirtualAddressSpace Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostMemoryManager.AcquiredVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: af80a43b86b1a16c5afe2741cb3d2bd7f0d874ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="f4f56-102">IHostMemoryManager::AcquiredVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4f56-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>
<span data-ttu-id="f4f56-103">Ana bilgisayar işletim sisteminden belirtilen bellek ortak dil çalışma zamanı (CLR) geçirmiş bildirir.</span><span class="sxs-lookup"><span data-stu-id="f4f56-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4f56-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4f56-104">Syntax</span></span>  
  
```  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4f56-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f4f56-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="f4f56-106">[in] Bellek başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="f4f56-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="f4f56-107">[in] Belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="f4f56-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4f56-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4f56-108">Remarks</span></span>  
 <span data-ttu-id="f4f56-109">`AcquiredVirtualAddressSpace` Yöntemi bir geri çağırma yöntemini ve barındırma uygulama yazıcı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4f56-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="f4f56-110">CLR tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f4f56-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4f56-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4f56-111">Requirements</span></span>  
 <span data-ttu-id="f4f56-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4f56-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4f56-113">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f4f56-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4f56-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f4f56-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4f56-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4f56-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4f56-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4f56-116">See Also</span></span>  
 [<span data-ttu-id="f4f56-117">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4f56-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
