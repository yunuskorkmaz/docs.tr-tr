---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugFrameEnum:: Next yöntemi'
title: ICorDebugFrameEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
ms.openlocfilehash: 67b7dd0282c07358f942990f8915150d6449fd32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692673"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="33965-103">ICorDebugFrameEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33965-103">ICorDebugFrameEnum::Next Method</span></span>

<span data-ttu-id="33965-104">Geçerli konumdan başlayarak, belirtilen ICorDebugFrame örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="33965-104">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33965-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33965-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33965-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="33965-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="33965-107">'ndaki `ICorDebugFrame` Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="33965-107">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="33965-108">dışı Her biri bir nesneye işaret eden işaretçiler dizisi `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="33965-108">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="33965-109">dışı Aslında döndürülen örnek sayısına yönelik bir işaretçi `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="33965-109">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="33965-110">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="33965-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33965-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33965-111">Requirements</span></span>  

 <span data-ttu-id="33965-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33965-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33965-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="33965-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33965-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="33965-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33965-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33965-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
