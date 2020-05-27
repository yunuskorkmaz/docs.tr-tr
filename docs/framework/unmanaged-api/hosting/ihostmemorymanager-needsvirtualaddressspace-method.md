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
ms.openlocfilehash: bb13c7329c558aa92ec65237aa8a9963c82fe1dc
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804520"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="7e3e4-102">IHostMemoryManager::NeedsVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e3e4-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="7e3e4-103">Ana bilgisayarı ortak dil çalışma zamanının (CLR) belirtilen belleği kullanmayı deneyeceği konusunda bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e3e4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7e3e4-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e3e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e3e4-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="7e3e4-106">'ndaki Belleğin başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="7e3e4-107">'ndaki Belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e3e4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e3e4-108">Remarks</span></span>  
 <span data-ttu-id="7e3e4-109">`NeedsVirtualAddressSpace`Yöntemi bir geri çağırma yöntemidir ve barındırma uygulamasının yazarı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="7e3e4-110">CLR tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="7e3e4-111">Ana bilgisayar CLR 'nin belirtilen belleği kullanmasını istemiyor bir HRESULT E_OUTOFMEMORY döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e3e4-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e3e4-112">Requirements</span></span>  
 <span data-ttu-id="7e3e4-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e3e4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e3e4-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7e3e4-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e3e4-115">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7e3e4-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e3e4-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e3e4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e3e4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-117">See also</span></span>

- [<span data-ttu-id="7e3e4-118">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e3e4-118">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
