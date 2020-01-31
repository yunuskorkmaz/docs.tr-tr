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
ms.openlocfilehash: 51c06a7f8ea22fc73236131954781d8755274041
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789083"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="5e5fc-102">ICLRDataTarget2::AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e5fc-102">ICLRDataTarget2::AllocVirtual Method</span></span>
<span data-ttu-id="5e5fc-103">Bu hedef işlemin adres alanına bellek ayırmak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="5e5fc-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e5fc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e5fc-104">Syntax</span></span>  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e5fc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e5fc-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="5e5fc-106">'ndaki Ayrılacak belleğin istenen başlangıç adresini belirten bir `CLRDATA_ADDRESS` değeri.</span><span class="sxs-lookup"><span data-stu-id="5e5fc-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="5e5fc-107">'ndaki Ayrılacak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="5e5fc-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="5e5fc-108">'ndaki Bellek ayırmayı denetleyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="5e5fc-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="5e5fc-109">Bkz. Win32 `VirtualAlloc` işlevi.</span><span class="sxs-lookup"><span data-stu-id="5e5fc-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="5e5fc-110">'ndaki Ayrılan bellek için koruma öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="5e5fc-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="5e5fc-111">Bkz. Win32 `VirtualAlloc` işlevi.</span><span class="sxs-lookup"><span data-stu-id="5e5fc-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="5e5fc-112">dışı Ayrılan belleğin gerçek başlangıç adresini belirten `CLRDATA_ADDRESS` değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5e5fc-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e5fc-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e5fc-113">Remarks</span></span>  
 <span data-ttu-id="5e5fc-114">`AllocVirtual` yöntemi, Win32 `VirtualAlloc` işlevi için bir mantıksal sarmalayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="5e5fc-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="5e5fc-115">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5e5fc-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e5fc-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e5fc-116">Requirements</span></span>  
 <span data-ttu-id="5e5fc-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e5fc-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e5fc-118">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="5e5fc-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5e5fc-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5e5fc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e5fc-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e5fc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e5fc-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e5fc-121">See also</span></span>

- [<span data-ttu-id="5e5fc-122">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e5fc-122">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="5e5fc-123">FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e5fc-123">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)
