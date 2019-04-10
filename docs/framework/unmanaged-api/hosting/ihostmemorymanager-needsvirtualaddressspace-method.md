---
title: IHostMemoryManager::NeedsVirtualAddressSpace Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0f029c8fbab97afe3089956391e8446d4cc5e15
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215501"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="a75d5-102">IHostMemoryManager::NeedsVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a75d5-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="a75d5-103">Konak, ortak dil çalışma zamanı (CLR) belirtilen bellek kullanma girişimi gittiği bildirir.</span><span class="sxs-lookup"><span data-stu-id="a75d5-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a75d5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a75d5-104">Syntax</span></span>  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a75d5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a75d5-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="a75d5-106">[in] Bellek başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="a75d5-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="a75d5-107">[in] Belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="a75d5-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a75d5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a75d5-108">Remarks</span></span>  
 <span data-ttu-id="a75d5-109">`NeedsVirtualAddressSpace` Yöntemi geri çağırma yöntemi olan ve uygulamanın barındırma yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a75d5-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="a75d5-110">CLR tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="a75d5-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="a75d5-111">Konak belirtilen bellek kullanmak için CLR istemiyorsa E_OUTOFMEMORY HRESULT döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="a75d5-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a75d5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a75d5-112">Requirements</span></span>  
 <span data-ttu-id="a75d5-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a75d5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a75d5-114">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a75d5-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a75d5-115">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a75d5-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="a75d5-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="a75d5-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a75d5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a75d5-117">See also</span></span>

- [<span data-ttu-id="a75d5-118">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a75d5-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
