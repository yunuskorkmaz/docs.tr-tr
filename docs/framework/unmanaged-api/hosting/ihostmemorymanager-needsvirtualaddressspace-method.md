---
title: "IHostMemoryManager::NeedsVirtualAddressSpace Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.NeedsVirtualAddressSpace
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9251cbadaf182cda8d52f3f5792452310561c376
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="5ac6c-102">IHostMemoryManager::NeedsVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ac6c-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="5ac6c-103">Ortak dil çalışma zamanı (CLR) belirtilen bellek kullanma girişimi gittiği konak bildirir.</span><span class="sxs-lookup"><span data-stu-id="5ac6c-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ac6c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ac6c-104">Syntax</span></span>  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ac6c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ac6c-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="5ac6c-106">[in] Bellek başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="5ac6c-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="5ac6c-107">[in] Belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="5ac6c-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ac6c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ac6c-108">Remarks</span></span>  
 <span data-ttu-id="5ac6c-109">`NeedsVirtualAddressSpace` Yöntemi bir geri çağırma yöntemini ve barındırma uygulama yazıcı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5ac6c-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="5ac6c-110">CLR tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5ac6c-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="5ac6c-111">Konak belirtilen bellek kullanmak için CLR istemiyorsa E_OUTOFMEMORY HRESULT döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="5ac6c-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ac6c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ac6c-112">Requirements</span></span>  
 <span data-ttu-id="5ac6c-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ac6c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ac6c-114">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5ac6c-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ac6c-115">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5ac6c-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ac6c-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ac6c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ac6c-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ac6c-117">See Also</span></span>  
 [<span data-ttu-id="5ac6c-118">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ac6c-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
