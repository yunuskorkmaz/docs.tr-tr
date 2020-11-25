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
ms.openlocfilehash: 6d3985919ea7e766db7d07e4ed81484851156ca5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723678"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="aefe9-102">ICLRDataTarget2::AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aefe9-102">ICLRDataTarget2::AllocVirtual Method</span></span>

<span data-ttu-id="aefe9-103">Bu hedef işlemin adres alanına bellek ayırmak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="aefe9-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aefe9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="aefe9-104">Syntax</span></span>  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aefe9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aefe9-105">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="aefe9-106">'ndaki `CLRDATA_ADDRESS` Ayrılacak belleğin istenen başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="aefe9-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="aefe9-107">'ndaki Ayrılacak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="aefe9-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="aefe9-108">'ndaki Bellek ayırmayı denetleyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="aefe9-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="aefe9-109">Bkz. Win32 `VirtualAlloc` işlevi.</span><span class="sxs-lookup"><span data-stu-id="aefe9-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="aefe9-110">'ndaki Ayrılan bellek için koruma öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="aefe9-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="aefe9-111">Bkz. Win32 `VirtualAlloc` işlevi.</span><span class="sxs-lookup"><span data-stu-id="aefe9-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="aefe9-112">dışı `CLRDATA_ADDRESS` Ayrılan belleğin gerçek başlangıç adresini belirten bir değer işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="aefe9-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aefe9-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aefe9-113">Remarks</span></span>  

 <span data-ttu-id="aefe9-114">`AllocVirtual`Yöntemi, Win32 işlevi için bir mantıksal sarmalayıcı görevi görür `VirtualAlloc` .</span><span class="sxs-lookup"><span data-stu-id="aefe9-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="aefe9-115">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="aefe9-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aefe9-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aefe9-116">Requirements</span></span>  

 <span data-ttu-id="aefe9-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aefe9-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aefe9-118">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="aefe9-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="aefe9-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="aefe9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aefe9-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aefe9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aefe9-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aefe9-121">See also</span></span>

- [<span data-ttu-id="aefe9-122">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aefe9-122">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="aefe9-123">FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aefe9-123">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)
