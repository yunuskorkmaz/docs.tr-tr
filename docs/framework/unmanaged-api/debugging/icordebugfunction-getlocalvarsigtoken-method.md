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
ms.openlocfilehash: c159a175ddd380015cc2dc21637c8b63fd3caea6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137893"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="a950a-102">ICorDebugFunction::GetLocalVarSigToken Metodu</span><span class="sxs-lookup"><span data-stu-id="a950a-102">ICorDebugFunction::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="a950a-103">Bu ICorDebugFunction örneğiyle temsil edilen işlevin yerel değişken imzası için meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="a950a-103">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a950a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a950a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a950a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a950a-105">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="a950a-106">dışı Bu işlevin yerel değişken imzası için `mdSignature` belirteç işaretçisi veya bu işlevin yerel değişkenleri yoksa `mdSignatureNil`.</span><span class="sxs-lookup"><span data-stu-id="a950a-106">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a950a-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a950a-107">Requirements</span></span>  
 <span data-ttu-id="a950a-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a950a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a950a-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a950a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a950a-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a950a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a950a-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a950a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
