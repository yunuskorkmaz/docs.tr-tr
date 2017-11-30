---
title: "ICLRDataTarget2::AllocVirtual Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget2.AllocVirtual
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e61b27ae7dcda8cc5e14d9c0f72f74c8bda13169
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="af9b4-102">ICLRDataTarget2::AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af9b4-102">ICLRDataTarget2::AllocVirtual Method</span></span>
<span data-ttu-id="af9b4-103">Bu hedef işlem adres alanındaki bellek ayıramadı ortak dil çalışma zamanı (CLR) veri erişim hizmeti tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="af9b4-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af9b4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af9b4-104">Syntax</span></span>  
  
```  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af9b4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af9b4-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="af9b4-106">[in] A `CLRDATA_ADDRESS` ayrılacak bellek istenen başlangıç adresini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="af9b4-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="af9b4-107">[in] Ayrılacak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="af9b4-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="af9b4-108">[in] Bellek ayırma kontrol bayraklar.</span><span class="sxs-lookup"><span data-stu-id="af9b4-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="af9b4-109">Win32 bkz `VirtualAlloc` işlevi.</span><span class="sxs-lookup"><span data-stu-id="af9b4-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="af9b4-110">[in] Ayrılan belleğin koruması öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="af9b4-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="af9b4-111">Win32 bkz `VirtualAlloc` işlevi.</span><span class="sxs-lookup"><span data-stu-id="af9b4-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="af9b4-112">[out] Bir işaretçi bir `CLRDATA_ADDRESS` ayrılmış bellek gerçek başlangıç adresini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="af9b4-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af9b4-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af9b4-113">Remarks</span></span>  
 <span data-ttu-id="af9b4-114">`AllocVirtual` Yöntemi Win32 için mantıksal bir kapsayıcı olarak hizmet veren `VirtualAlloc` işlevi.</span><span class="sxs-lookup"><span data-stu-id="af9b4-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="af9b4-115">Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="af9b4-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af9b4-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af9b4-116">Requirements</span></span>  
 <span data-ttu-id="af9b4-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af9b4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af9b4-118">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="af9b4-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="af9b4-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af9b4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af9b4-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af9b4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af9b4-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="af9b4-121">See Also</span></span>  
 [<span data-ttu-id="af9b4-122">Iclrdatatarget2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="af9b4-122">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="af9b4-123">FreeVirtual yöntemi</span><span class="sxs-lookup"><span data-stu-id="af9b4-123">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
