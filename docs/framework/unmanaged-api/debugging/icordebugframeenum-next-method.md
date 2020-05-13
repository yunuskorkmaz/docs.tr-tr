---
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
ms.openlocfilehash: 4652e4b34d614ad3b7b852925fcc63309bdd1498
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209467"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="ac5fb-102">ICorDebugFrameEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac5fb-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="ac5fb-103">Geçerli konumdan başlayarak, belirtilen ICorDebugFrame örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="ac5fb-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac5fb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac5fb-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac5fb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac5fb-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ac5fb-106">'ndaki `ICorDebugFrame`Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="ac5fb-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="ac5fb-107">dışı Her biri bir nesneye işaret eden işaretçiler dizisi `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="ac5fb-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ac5fb-108">dışı Aslında döndürülen örnek sayısına yönelik bir işaretçi `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="ac5fb-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="ac5fb-109">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="ac5fb-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac5fb-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac5fb-110">Requirements</span></span>  
 <span data-ttu-id="ac5fb-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac5fb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac5fb-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ac5fb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac5fb-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ac5fb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac5fb-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac5fb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
