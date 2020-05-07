---
title: ICorDebugAssemblyEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum::Next method
helpviewer_keywords:
- ICorDebugAssemblyEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: b3e7d0c2-3baa-4ef8-8e3f-b865cf252940
topic_type:
- apiref
ms.openlocfilehash: 155354b335caf83c466c8d9d6711f36c7efc9298
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894808"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="5e12e-102">ICorDebugAssemblyEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e12e-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="5e12e-103">Geçerli imleç konumundan başlayarak koleksiyondan belirtilen sayıda derlemeyi alır.</span><span class="sxs-lookup"><span data-stu-id="5e12e-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e12e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e12e-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e12e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e12e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5e12e-106">'ndaki Alınacak derleme sayısı.</span><span class="sxs-lookup"><span data-stu-id="5e12e-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="5e12e-107">dışı Her biri bir derlemeyi temsil eden ICorDebugAssembly nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="5e12e-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="5e12e-108">dışı Aslında döndürülen derleme sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5e12e-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="5e12e-109">Bu değer bir `celt` ise null olabilir.</span><span class="sxs-lookup"><span data-stu-id="5e12e-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e12e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e12e-110">Requirements</span></span>  
 <span data-ttu-id="5e12e-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e12e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e12e-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5e12e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e12e-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5e12e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e12e-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e12e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
