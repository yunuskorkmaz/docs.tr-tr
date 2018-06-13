---
title: CreateAssemblyEnum İşlevi
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2098d5d9ce1c01f232cf2904c1fd3e990dfbe2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432122"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="35f45-102">CreateAssemblyEnum İşlevi</span><span class="sxs-lookup"><span data-stu-id="35f45-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="35f45-103">Bir işaretçi alır bir [Iassemblyenum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) Belirtilen derlemedeki nesneleri listeleme örneği [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="35f45-103">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35f45-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35f45-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35f45-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35f45-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="35f45-106">[out] İstenen içeren bir bellek konumunu işaretçi `IAssemblyEnum` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="35f45-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="35f45-107">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="35f45-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="35f45-108">`pUnkReserved` bir null başvuru olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="35f45-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="35f45-109">[in] `IAssemblyName` İstenen derlemenin.</span><span class="sxs-lookup"><span data-stu-id="35f45-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="35f45-110">Bu ad numaralandırma filtrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="35f45-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="35f45-111">Tüm derlemeleri genel derleme önbelleğinde Numaralandırılacak null olabilir.</span><span class="sxs-lookup"><span data-stu-id="35f45-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="35f45-112">[in] Numaralandırıcının davranışını değiştirmek için işaretler.</span><span class="sxs-lookup"><span data-stu-id="35f45-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="35f45-113">Bu parametre tam olarak bir bit içerir [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="35f45-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="35f45-114">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="35f45-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="35f45-115">`pvReserved` bir null başvuru olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="35f45-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35f45-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35f45-116">Remarks</span></span>  
 <span data-ttu-id="35f45-117">`dwFlags` Parametre içeren tam olarak bir bit `ASM_CACHE_FLAGS` numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="35f45-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35f45-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35f45-118">Requirements</span></span>  
 <span data-ttu-id="35f45-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35f45-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35f45-120">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="35f45-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="35f45-121">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="35f45-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="35f45-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35f45-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35f45-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35f45-123">See Also</span></span>  
 [<span data-ttu-id="35f45-124">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35f45-124">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 [<span data-ttu-id="35f45-125">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35f45-125">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="35f45-126">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="35f45-126">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
