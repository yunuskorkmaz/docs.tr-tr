---
title: "CreateAssemblyEnum İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateAssemblyEnum
helpviewer_keywords: CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3719da442b2c2c589772a0bc19cec3efb4e6dace
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="60495-102">CreateAssemblyEnum İşlevi</span><span class="sxs-lookup"><span data-stu-id="60495-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="60495-103">Bir işaretçi alır bir [Iassemblyenum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) Belirtilen derlemedeki nesneleri listeleme örneği [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="60495-103">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60495-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60495-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60495-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="60495-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="60495-106">[out] İstenen içeren bir bellek konumunu işaretçi `IAssemblyEnum` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="60495-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="60495-107">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="60495-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="60495-108">`pUnkReserved`bir null başvuru olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="60495-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="60495-109">[in] `IAssemblyName` İstenen derlemenin.</span><span class="sxs-lookup"><span data-stu-id="60495-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="60495-110">Bu ad numaralandırma filtrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60495-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="60495-111">Tüm derlemeleri genel derleme önbelleğinde Numaralandırılacak null olabilir.</span><span class="sxs-lookup"><span data-stu-id="60495-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="60495-112">[in] Numaralandırıcının davranışını değiştirmek için işaretler.</span><span class="sxs-lookup"><span data-stu-id="60495-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="60495-113">Bu parametre tam olarak bir bit içerir [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="60495-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="60495-114">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="60495-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="60495-115">`pvReserved`bir null başvuru olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="60495-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60495-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60495-116">Remarks</span></span>  
 <span data-ttu-id="60495-117">`dwFlags` Parametre içeren tam olarak bir bit `ASM_CACHE_FLAGS` numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="60495-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60495-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60495-118">Requirements</span></span>  
 <span data-ttu-id="60495-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60495-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60495-120">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="60495-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="60495-121">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="60495-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="60495-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60495-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60495-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60495-123">See Also</span></span>  
 [<span data-ttu-id="60495-124">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60495-124">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 [<span data-ttu-id="60495-125">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60495-125">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="60495-126">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="60495-126">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
