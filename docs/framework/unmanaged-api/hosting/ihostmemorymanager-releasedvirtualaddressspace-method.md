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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f337ece4e68c1685f7474df4b96074597e16271a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501428"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="c55e5-102">IHostMemoryManager::ReleasedVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c55e5-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="c55e5-103">Konak, ortak dil çalışma zamanı (CLR) belirtilen bellek kullanarak tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="c55e5-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c55e5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c55e5-104">Syntax</span></span>  
  
```  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c55e5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c55e5-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="c55e5-106">[in] Başlangıç adresi serbest bırakılacak bellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c55e5-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c55e5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c55e5-107">Remarks</span></span>  
 <span data-ttu-id="c55e5-108">`ReleasedVirtualAddressSpace` Yöntemi geri çağırma yöntemi olan ve uygulamanın barındırma yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c55e5-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="c55e5-109">CLR tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="c55e5-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c55e5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c55e5-110">Requirements</span></span>  
 <span data-ttu-id="c55e5-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c55e5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c55e5-112">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c55e5-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c55e5-113">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c55e5-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c55e5-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c55e5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c55e5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c55e5-115">See also</span></span>
- [<span data-ttu-id="c55e5-116">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c55e5-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
