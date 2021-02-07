---
description: 'Şu konuda daha fazla bilgi edinin: IHostMemoryManager:: gereksiz Svirtualaddressspace yöntemi'
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
ms.openlocfilehash: 95d4128decffc82fdcb198155b48a31420f71220
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707793"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="05afe-103">IHostMemoryManager::NeedsVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05afe-103">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>

<span data-ttu-id="05afe-104">Ana bilgisayarı ortak dil çalışma zamanının (CLR) belirtilen belleği kullanmayı deneyeceği konusunda bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="05afe-104">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05afe-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05afe-105">Syntax</span></span>  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05afe-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05afe-106">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="05afe-107">'ndaki Belleğin başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="05afe-107">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="05afe-108">'ndaki Belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="05afe-108">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05afe-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05afe-109">Remarks</span></span>  

 <span data-ttu-id="05afe-110">`NeedsVirtualAddressSpace`Yöntemi bir geri çağırma yöntemidir ve barındırma uygulamasının yazarı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05afe-110">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="05afe-111">CLR tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="05afe-111">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="05afe-112">Ana bilgisayar CLR 'nin belirtilen belleği kullanmasını istemiyor bir HRESULT E_OUTOFMEMORY döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="05afe-112">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05afe-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05afe-113">Requirements</span></span>  

 <span data-ttu-id="05afe-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05afe-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05afe-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="05afe-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05afe-116">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="05afe-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05afe-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05afe-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05afe-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05afe-118">See also</span></span>

- [<span data-ttu-id="05afe-119">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05afe-119">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
