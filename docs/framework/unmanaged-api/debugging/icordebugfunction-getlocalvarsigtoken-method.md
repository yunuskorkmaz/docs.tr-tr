---
title: ICorDebugFunction::GetLocalVarSigToken Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetLocalVarSigToken
helpviewer_keywords:
- ICorDebugFunction::GetLocalVarSigToken method [.NET Framework debugging]
- GetLocalVarSigToken method [.NET Framework debugging]
ms.assetid: 31e53494-bcc9-4981-91a4-f7e0f02cad48
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e03e7a965bc923d91cb0c83a9ea8ea5899da63a9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754661"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="63c1e-102">ICorDebugFunction::GetLocalVarSigToken Metodu</span><span class="sxs-lookup"><span data-stu-id="63c1e-102">ICorDebugFunction::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="63c1e-103">Meta veriler için yerel değişken bu ICorDebugFunction örneği tarafından temsil edilen işlev imzası belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="63c1e-103">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63c1e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63c1e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63c1e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63c1e-105">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="63c1e-106">[out] Bir işaretçi `mdSignature` bu işlev yerel değişken imzası belirteci veya `mdSignatureNil`, bu işlev yerel değişken yok.</span><span class="sxs-lookup"><span data-stu-id="63c1e-106">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63c1e-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63c1e-107">Requirements</span></span>  
 <span data-ttu-id="63c1e-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63c1e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63c1e-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63c1e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63c1e-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63c1e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63c1e-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63c1e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
