---
description: 'Daha fazla bilgi edinin: ICLRDataTarget2:: AllocVirtual Yöntemi'
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
ms.openlocfilehash: d81474e4067599178285b6fa876919298617919d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729347"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="07f80-103">ICLRDataTarget2::AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07f80-103">ICLRDataTarget2::AllocVirtual Method</span></span>

<span data-ttu-id="07f80-104">Bu hedef işlemin adres alanına bellek ayırmak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="07f80-104">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07f80-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07f80-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07f80-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07f80-106">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="07f80-107">'ndaki `CLRDATA_ADDRESS` Ayrılacak belleğin istenen başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="07f80-107">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="07f80-108">'ndaki Ayrılacak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="07f80-108">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="07f80-109">'ndaki Bellek ayırmayı denetleyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="07f80-109">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="07f80-110">Bkz. Win32 `VirtualAlloc` işlevi.</span><span class="sxs-lookup"><span data-stu-id="07f80-110">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="07f80-111">'ndaki Ayrılan bellek için koruma öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="07f80-111">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="07f80-112">Bkz. Win32 `VirtualAlloc` işlevi.</span><span class="sxs-lookup"><span data-stu-id="07f80-112">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="07f80-113">dışı `CLRDATA_ADDRESS` Ayrılan belleğin gerçek başlangıç adresini belirten bir değer işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="07f80-113">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07f80-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07f80-114">Remarks</span></span>  

 <span data-ttu-id="07f80-115">`AllocVirtual`Yöntemi, Win32 işlevi için bir mantıksal sarmalayıcı görevi görür `VirtualAlloc` .</span><span class="sxs-lookup"><span data-stu-id="07f80-115">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="07f80-116">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="07f80-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07f80-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07f80-117">Requirements</span></span>  

 <span data-ttu-id="07f80-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07f80-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07f80-119">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="07f80-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="07f80-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="07f80-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07f80-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07f80-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f80-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07f80-122">See also</span></span>

- [<span data-ttu-id="07f80-123">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07f80-123">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="07f80-124">FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07f80-124">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)
