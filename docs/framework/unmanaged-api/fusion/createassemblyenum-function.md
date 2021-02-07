---
description: ': CreateAssemblyEnum Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 47177fcf0cd9e1b492fa89b9fb80c5cdaaced689
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761149"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="86c7e-103">CreateAssemblyEnum İşlevi</span><span class="sxs-lookup"><span data-stu-id="86c7e-103">CreateAssemblyEnum Function</span></span>

<span data-ttu-id="86c7e-104">Derlemedeki nesneleri belirtilen [IAssemblyName](iassemblyname-interface.md)ile numaralandıracak bir [IAssemblyEnum](iassemblyenum-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="86c7e-104">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86c7e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86c7e-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="86c7e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86c7e-106">Parameters</span></span>  

 `pEnum`  
 <span data-ttu-id="86c7e-107">dışı İstenen işaretçiyi içeren bir bellek konumu işaretçisi `IAssemblyEnum` .</span><span class="sxs-lookup"><span data-stu-id="86c7e-107">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="86c7e-108">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="86c7e-108">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="86c7e-109">`pUnkReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86c7e-109">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="86c7e-110">'ndaki `IAssemblyName` İstenen derlemenin ' i.</span><span class="sxs-lookup"><span data-stu-id="86c7e-110">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="86c7e-111">Bu ad, numaralandırmayı filtrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86c7e-111">This name is used to filter the enumeration.</span></span> <span data-ttu-id="86c7e-112">Genel derleme önbelleğindeki tüm derlemeleri listelemek için null olabilir.</span><span class="sxs-lookup"><span data-stu-id="86c7e-112">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="86c7e-113">'ndaki Numaralandırıcının davranışını değiştirme bayrakları.</span><span class="sxs-lookup"><span data-stu-id="86c7e-113">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="86c7e-114">Bu parametre [asm_cache_flags](asm-cache-flags-enumeration.md) numaralandırmasından tam olarak bir bit içerir.</span><span class="sxs-lookup"><span data-stu-id="86c7e-114">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="86c7e-115">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="86c7e-115">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="86c7e-116">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86c7e-116">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86c7e-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86c7e-117">Remarks</span></span>  

 <span data-ttu-id="86c7e-118">`dwFlags`Parametresi Numaralandırmadaki tam olarak bir bit içeriyor `ASM_CACHE_FLAGS` .</span><span class="sxs-lookup"><span data-stu-id="86c7e-118">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86c7e-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86c7e-119">Requirements</span></span>  

 <span data-ttu-id="86c7e-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86c7e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86c7e-121">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="86c7e-121">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="86c7e-122">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="86c7e-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="86c7e-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86c7e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c7e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86c7e-124">See also</span></span>

- [<span data-ttu-id="86c7e-125">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86c7e-125">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
- [<span data-ttu-id="86c7e-126">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86c7e-126">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="86c7e-127">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="86c7e-127">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
