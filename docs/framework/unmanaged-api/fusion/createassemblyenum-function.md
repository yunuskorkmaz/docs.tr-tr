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
ms.openlocfilehash: d809bbfa17ed9e9ae16505852740e874ca11248c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621792"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="47ce3-102">CreateAssemblyEnum İşlevi</span><span class="sxs-lookup"><span data-stu-id="47ce3-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="47ce3-103">Bir işaretçi alır bir [Iassemblyenum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) nesneleri ile belirtilen derlemedeki numaralandırabilirsiniz örneği [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="47ce3-103">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47ce3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47ce3-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47ce3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47ce3-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="47ce3-106">[out] İstenen içeren bir bellek konumuna işaretçi `IAssemblyEnum` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="47ce3-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="47ce3-107">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="47ce3-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="47ce3-108">`pUnkReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47ce3-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="47ce3-109">[in] `IAssemblyName` İstenen derleme.</span><span class="sxs-lookup"><span data-stu-id="47ce3-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="47ce3-110">Bu ad, numaralandırma filtrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47ce3-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="47ce3-111">Genel derleme önbelleğini tüm derlemeleri numaralandırmak için null olabilir.</span><span class="sxs-lookup"><span data-stu-id="47ce3-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="47ce3-112">[in] Numaralandırıcının davranışını değiştirmek için kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="47ce3-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="47ce3-113">Bu parametre içeren tam bir bit [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="47ce3-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="47ce3-114">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="47ce3-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="47ce3-115">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47ce3-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47ce3-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47ce3-116">Remarks</span></span>  
 <span data-ttu-id="47ce3-117">`dwFlags` Parametre içeren tam bir bit `ASM_CACHE_FLAGS` sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="47ce3-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47ce3-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47ce3-118">Requirements</span></span>  
 <span data-ttu-id="47ce3-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47ce3-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47ce3-120">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="47ce3-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="47ce3-121">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="47ce3-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="47ce3-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47ce3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47ce3-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47ce3-123">See also</span></span>
- [<span data-ttu-id="47ce3-124">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47ce3-124">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
- [<span data-ttu-id="47ce3-125">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47ce3-125">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="47ce3-126">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="47ce3-126">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
