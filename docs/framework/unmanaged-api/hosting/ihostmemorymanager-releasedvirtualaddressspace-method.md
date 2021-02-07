---
description: 'Şu konuda daha fazla bilgi edinin: IHostMemoryManager:: ReleasedVirtualAddressSpace Yöntemi'
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
ms.openlocfilehash: e67e80018b5002bdf2a50530af9ab057696fff4c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707780"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="f4bd0-103">IHostMemoryManager::ReleasedVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4bd0-103">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>

<span data-ttu-id="f4bd0-104">Ana bilgisayara, ortak dil çalışma zamanının (CLR) belirtilen belleği kullanarak tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="f4bd0-104">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4bd0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4bd0-105">Syntax</span></span>  
  
```cpp  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4bd0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f4bd0-106">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="f4bd0-107">'ndaki Yayımlanacak belleğin başlangıç adresi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f4bd0-107">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4bd0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4bd0-108">Remarks</span></span>  

 <span data-ttu-id="f4bd0-109">`ReleasedVirtualAddressSpace`Yöntemi bir geri çağırma yöntemidir ve barındırma uygulamasının yazarı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4bd0-109">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="f4bd0-110">CLR tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="f4bd0-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4bd0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4bd0-111">Requirements</span></span>  

 <span data-ttu-id="f4bd0-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4bd0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4bd0-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f4bd0-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4bd0-114">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f4bd0-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4bd0-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4bd0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4bd0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4bd0-116">See also</span></span>

- [<span data-ttu-id="f4bd0-117">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4bd0-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
