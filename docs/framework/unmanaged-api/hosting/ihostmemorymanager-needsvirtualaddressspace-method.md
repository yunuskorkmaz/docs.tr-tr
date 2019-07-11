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
ms.openlocfilehash: 57ed64ad8a6ae8ef46f423471436c3fce29d6fe5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767813"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="65ca1-102">IHostMemoryManager::NeedsVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65ca1-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="65ca1-103">Konak, ortak dil çalışma zamanı (CLR) belirtilen bellek kullanma girişimi gittiği bildirir.</span><span class="sxs-lookup"><span data-stu-id="65ca1-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65ca1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65ca1-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65ca1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65ca1-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="65ca1-106">[in] Bellek başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="65ca1-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="65ca1-107">[in] Belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="65ca1-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65ca1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65ca1-108">Remarks</span></span>  
 <span data-ttu-id="65ca1-109">`NeedsVirtualAddressSpace` Yöntemi geri çağırma yöntemi olan ve uygulamanın barındırma yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="65ca1-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="65ca1-110">CLR tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="65ca1-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="65ca1-111">Konak belirtilen bellek kullanmak için CLR istemiyorsa E_OUTOFMEMORY HRESULT döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="65ca1-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65ca1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65ca1-112">Requirements</span></span>  
 <span data-ttu-id="65ca1-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65ca1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65ca1-114">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="65ca1-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65ca1-115">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="65ca1-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65ca1-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65ca1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ca1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65ca1-117">See also</span></span>

- [<span data-ttu-id="65ca1-118">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65ca1-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
