---
title: "ICorDebugAssemblyEnum::Next Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssemblyEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssemblyEnum::Next method
helpviewer_keywords:
- ICorDebugAssemblyEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: b3e7d0c2-3baa-4ef8-8e3f-b865cf252940
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a7430a420769a2d7952caf93af3b1412094483f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="6f766-102">ICorDebugAssemblyEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f766-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="6f766-103">Geçerli İmleç konumuna başlangıç koleksiyondan derlemeleri belirtilen sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="6f766-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f766-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f766-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f766-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f766-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6f766-106">[in] Alınacak derlemeleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="6f766-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="6f766-107">[out] Her biri bir derlemeyi temsil eden bir Icordebugassembly bir nesneye işaret etmiyor dizisi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6f766-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6f766-108">[out] Gerçekte döndürülen derlemeleri sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6f766-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="6f766-109">Bu değer null ise `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="6f766-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f766-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f766-110">Requirements</span></span>  
 <span data-ttu-id="6f766-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f766-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f766-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f766-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f766-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f766-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f766-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f766-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
