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
ms.openlocfilehash: b7e3696121475885f5061bd96eb6905d7ccae734
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683179"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="8bcbd-102">CreateAssemblyEnum İşlevi</span><span class="sxs-lookup"><span data-stu-id="8bcbd-102">CreateAssemblyEnum Function</span></span>

<span data-ttu-id="8bcbd-103">Derlemedeki nesneleri belirtilen [IAssemblyName](iassemblyname-interface.md)ile numaralandıracak bir [IAssemblyEnum](iassemblyenum-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="8bcbd-103">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bcbd-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8bcbd-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bcbd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8bcbd-105">Parameters</span></span>  

 `pEnum`  
 <span data-ttu-id="8bcbd-106">dışı İstenen işaretçiyi içeren bir bellek konumu işaretçisi `IAssemblyEnum` .</span><span class="sxs-lookup"><span data-stu-id="8bcbd-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="8bcbd-107">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="8bcbd-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="8bcbd-108">`pUnkReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bcbd-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="8bcbd-109">'ndaki `IAssemblyName` İstenen derlemenin ' i.</span><span class="sxs-lookup"><span data-stu-id="8bcbd-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="8bcbd-110">Bu ad, numaralandırmayı filtrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8bcbd-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="8bcbd-111">Genel derleme önbelleğindeki tüm derlemeleri listelemek için null olabilir.</span><span class="sxs-lookup"><span data-stu-id="8bcbd-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8bcbd-112">'ndaki Numaralandırıcının davranışını değiştirme bayrakları.</span><span class="sxs-lookup"><span data-stu-id="8bcbd-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="8bcbd-113">Bu parametre [asm_cache_flags](asm-cache-flags-enumeration.md) numaralandırmasından tam olarak bir bit içerir.</span><span class="sxs-lookup"><span data-stu-id="8bcbd-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="8bcbd-114">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="8bcbd-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="8bcbd-115">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bcbd-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bcbd-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8bcbd-116">Remarks</span></span>  

 <span data-ttu-id="8bcbd-117">`dwFlags`Parametresi Numaralandırmadaki tam olarak bir bit içeriyor `ASM_CACHE_FLAGS` .</span><span class="sxs-lookup"><span data-stu-id="8bcbd-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bcbd-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8bcbd-118">Requirements</span></span>  

 <span data-ttu-id="8bcbd-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bcbd-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bcbd-120">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="8bcbd-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8bcbd-121">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8bcbd-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8bcbd-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bcbd-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bcbd-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bcbd-123">See also</span></span>

- [<span data-ttu-id="8bcbd-124">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8bcbd-124">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
- [<span data-ttu-id="8bcbd-125">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8bcbd-125">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="8bcbd-126">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="8bcbd-126">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
