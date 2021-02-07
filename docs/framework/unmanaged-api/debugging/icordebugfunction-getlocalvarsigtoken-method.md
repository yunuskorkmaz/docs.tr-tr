---
description: ': ICorDebugFunction:: GetLocalVarSigToken yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: cd7fb03829285ddcb1da2f1a93985fa1f98d3d39
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692504"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="c3f29-103">ICorDebugFunction::GetLocalVarSigToken Metodu</span><span class="sxs-lookup"><span data-stu-id="c3f29-103">ICorDebugFunction::GetLocalVarSigToken Method</span></span>

<span data-ttu-id="c3f29-104">Bu ICorDebugFunction örneğiyle temsil edilen işlevin yerel değişken imzası için meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="c3f29-104">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3f29-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3f29-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3f29-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3f29-106">Parameters</span></span>  

 `pmdSig`  
 <span data-ttu-id="c3f29-107">dışı `mdSignature` Bu işlevin yerel değişken imzası için belirteç işaretçisi veya `mdSignatureNil` Bu işlevin yerel değişkenleri yoksa.</span><span class="sxs-lookup"><span data-stu-id="c3f29-107">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3f29-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3f29-108">Requirements</span></span>  

 <span data-ttu-id="c3f29-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3f29-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3f29-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c3f29-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3f29-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c3f29-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3f29-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3f29-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
