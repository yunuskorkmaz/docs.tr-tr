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
ms.openlocfilehash: 8a875d59d270f087ce22079830818a9205309cc5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731299"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="b7028-102">IHostMemoryManager::ReleasedVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7028-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>

<span data-ttu-id="b7028-103">Ana bilgisayara, ortak dil çalışma zamanının (CLR) belirtilen belleği kullanarak tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="b7028-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7028-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b7028-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7028-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7028-105">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="b7028-106">'ndaki Yayımlanacak belleğin başlangıç adresi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b7028-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7028-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7028-107">Remarks</span></span>  

 <span data-ttu-id="b7028-108">`ReleasedVirtualAddressSpace`Yöntemi bir geri çağırma yöntemidir ve barındırma uygulamasının yazarı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b7028-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="b7028-109">CLR tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="b7028-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7028-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7028-110">Requirements</span></span>  

 <span data-ttu-id="b7028-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7028-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7028-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b7028-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b7028-113">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b7028-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7028-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7028-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7028-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7028-115">See also</span></span>

- [<span data-ttu-id="b7028-116">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7028-116">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
