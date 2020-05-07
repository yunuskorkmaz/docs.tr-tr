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
ms.openlocfilehash: 20b73549d30fe210e4d44902d2f459ea9c682360
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860487"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="4d5a6-102">ICLRDataTarget2::AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d5a6-102">ICLRDataTarget2::AllocVirtual Method</span></span>
<span data-ttu-id="4d5a6-103">Bu hedef işlemin adres alanına bellek ayırmak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="4d5a6-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d5a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d5a6-104">Syntax</span></span>  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d5a6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4d5a6-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="4d5a6-106">'ndaki Ayrılacak `CLRDATA_ADDRESS` belleğin istenen başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="4d5a6-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="4d5a6-107">'ndaki Ayrılacak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="4d5a6-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="4d5a6-108">'ndaki Bellek ayırmayı denetleyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="4d5a6-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="4d5a6-109">Bkz. Win32 `VirtualAlloc` işlevi.</span><span class="sxs-lookup"><span data-stu-id="4d5a6-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="4d5a6-110">'ndaki Ayrılan bellek için koruma öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="4d5a6-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="4d5a6-111">Bkz. Win32 `VirtualAlloc` işlevi.</span><span class="sxs-lookup"><span data-stu-id="4d5a6-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="4d5a6-112">dışı Ayrılan belleğin gerçek başlangıç `CLRDATA_ADDRESS` adresini belirten bir değer işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4d5a6-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d5a6-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d5a6-113">Remarks</span></span>  
 <span data-ttu-id="4d5a6-114">`AllocVirtual` Yöntemi, Win32 `VirtualAlloc` işlevi için bir mantıksal sarmalayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="4d5a6-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="4d5a6-115">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4d5a6-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d5a6-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d5a6-116">Requirements</span></span>  
 <span data-ttu-id="4d5a6-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d5a6-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d5a6-118">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="4d5a6-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4d5a6-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4d5a6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d5a6-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d5a6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d5a6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d5a6-121">See also</span></span>

- [<span data-ttu-id="4d5a6-122">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d5a6-122">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="4d5a6-123">FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d5a6-123">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)
