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
ms.openlocfilehash: 4a246fb95ab5b4a7f187aa660f20e590c63ddff2
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804464"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="dde68-102">IHostMemoryManager::ReleasedVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dde68-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="dde68-103">Ana bilgisayara, ortak dil çalışma zamanının (CLR) belirtilen belleği kullanarak tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="dde68-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dde68-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="dde68-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dde68-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dde68-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="dde68-106">'ndaki Yayımlanacak belleğin başlangıç adresi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="dde68-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dde68-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dde68-107">Remarks</span></span>  
 <span data-ttu-id="dde68-108">`ReleasedVirtualAddressSpace`Yöntemi bir geri çağırma yöntemidir ve barındırma uygulamasının yazarı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dde68-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="dde68-109">CLR tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="dde68-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dde68-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dde68-110">Requirements</span></span>  
 <span data-ttu-id="dde68-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dde68-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dde68-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dde68-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dde68-113">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="dde68-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dde68-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dde68-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dde68-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dde68-115">See also</span></span>

- [<span data-ttu-id="dde68-116">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dde68-116">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
