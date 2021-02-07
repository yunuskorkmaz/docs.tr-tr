---
description: 'Şu konuda daha fazla bilgi edinin: IHostMemoryManager:: AcquiredVirtualAddressSpace yöntemi'
title: IHostMemoryManager::AcquiredVirtualAddressSpace Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: 70424c5bf907cfc3fb2e8951464335323f9331f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707923"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="05808-103">IHostMemoryManager::AcquiredVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05808-103">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>

<span data-ttu-id="05808-104">Ana bilgisayara ortak dil çalışma zamanının (CLR) belirtilen belleği işletim sisteminden almış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="05808-104">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05808-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05808-105">Syntax</span></span>  
  
```cpp  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05808-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05808-106">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="05808-107">'ndaki Belleğin başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="05808-107">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="05808-108">'ndaki Belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="05808-108">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05808-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05808-109">Remarks</span></span>  

 <span data-ttu-id="05808-110">`AcquiredVirtualAddressSpace`Yöntemi bir geri çağırma yöntemidir ve barındırma uygulamasının yazarı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05808-110">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="05808-111">CLR tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="05808-111">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05808-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05808-112">Requirements</span></span>  

 <span data-ttu-id="05808-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05808-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05808-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="05808-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05808-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="05808-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05808-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05808-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05808-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05808-117">See also</span></span>

- [<span data-ttu-id="05808-118">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05808-118">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
