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
ms.openlocfilehash: 9a09741ed778436f1cb35d094885bd3effa813a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411600"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="4af83-102">ICorDebugFunction::GetLocalVarSigToken Metodu</span><span class="sxs-lookup"><span data-stu-id="4af83-102">ICorDebugFunction::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="4af83-103">Meta veriler bu ICorDebugFunction örneği tarafından temsil edilen işlevinin yerel değişken imzası belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="4af83-103">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4af83-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4af83-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4af83-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4af83-105">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="4af83-106">[out] Bir işaretçi `mdSignature` bu işlevin yerel değişken imza için belirteç veya `mdSignatureNil`, bu işlev yerel değişken yok.</span><span class="sxs-lookup"><span data-stu-id="4af83-106">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4af83-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4af83-107">Requirements</span></span>  
 <span data-ttu-id="4af83-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4af83-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4af83-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4af83-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4af83-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4af83-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4af83-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4af83-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
