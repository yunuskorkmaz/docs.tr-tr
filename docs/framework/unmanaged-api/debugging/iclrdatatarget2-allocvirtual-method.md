---
title: ICLRDataTarget2::AllocVirtual Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92eff65078f05557f542c64c1be7d4f6eca43eb5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738472"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="f509c-102">ICLRDataTarget2::AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f509c-102">ICLRDataTarget2::AllocVirtual Method</span></span>
<span data-ttu-id="f509c-103">Bu hedef işlemin adres alanında bellek ayırmak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f509c-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f509c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f509c-104">Syntax</span></span>  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f509c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f509c-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="f509c-106">[in] A `CLRDATA_ADDRESS` ayrılacak bellek istenen başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f509c-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="f509c-107">[in] Baytlarında ayrılacak bellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="f509c-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="f509c-108">[in] Bellek ayırma denetleyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="f509c-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="f509c-109">Win32 bkz `VirtualAlloc` işlevi.</span><span class="sxs-lookup"><span data-stu-id="f509c-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="f509c-110">[in] Ayrılan bellek koruması öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="f509c-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="f509c-111">Win32 bkz `VirtualAlloc` işlevi.</span><span class="sxs-lookup"><span data-stu-id="f509c-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="f509c-112">[out] Bir işaretçi bir `CLRDATA_ADDRESS` ayrılan bellek gerçek başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f509c-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f509c-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f509c-113">Remarks</span></span>  
 <span data-ttu-id="f509c-114">`AllocVirtual` Yöntemi Win32 için mantıksal kapsayıcı olarak hizmet veren `VirtualAlloc` işlevi.</span><span class="sxs-lookup"><span data-stu-id="f509c-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="f509c-115">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f509c-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f509c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f509c-116">Requirements</span></span>  
 <span data-ttu-id="f509c-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f509c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f509c-118">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="f509c-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f509c-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f509c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f509c-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f509c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f509c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f509c-121">See also</span></span>

- [<span data-ttu-id="f509c-122">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f509c-122">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="f509c-123">FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f509c-123">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
