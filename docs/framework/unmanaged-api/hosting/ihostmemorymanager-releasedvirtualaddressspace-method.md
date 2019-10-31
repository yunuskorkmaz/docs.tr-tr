---
title: IHostMemoryManager::ReleasedVirtualAddressSpace Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.ReleasedVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type:
- apiref
ms.openlocfilehash: 46082ddcee0163d5e61b3e468eb32c71e9f242ce
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128623"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="9bac5-102">IHostMemoryManager::ReleasedVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bac5-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="9bac5-103">Ana bilgisayara, ortak dil çalışma zamanının (CLR) belirtilen belleği kullanarak tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="9bac5-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bac5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bac5-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9bac5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9bac5-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="9bac5-106">'ndaki Yayımlanacak belleğin başlangıç adresi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9bac5-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bac5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9bac5-107">Remarks</span></span>  
 <span data-ttu-id="9bac5-108">`ReleasedVirtualAddressSpace` yöntemi bir geri çağırma yöntemidir ve barındırma uygulamasının yazarı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9bac5-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="9bac5-109">CLR tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="9bac5-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bac5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9bac5-110">Requirements</span></span>  
 <span data-ttu-id="9bac5-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bac5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bac5-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9bac5-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9bac5-113">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9bac5-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9bac5-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bac5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bac5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bac5-115">See also</span></span>

- [<span data-ttu-id="9bac5-116">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bac5-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
