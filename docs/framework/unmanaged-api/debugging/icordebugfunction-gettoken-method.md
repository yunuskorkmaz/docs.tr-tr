---
title: ICorDebugFunction::GetToken Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7edf1f9dadafd989197170123cb3cb470a5ea908
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="2f6e4-102">ICorDebugFunction::GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="2f6e4-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="2f6e4-103">Meta verileri bu işlev için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="2f6e4-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f6e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f6e4-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f6e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2f6e4-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="2f6e4-106">[out] Bir işaretçi bir `mdMethodDef` bu işlev için meta veriler başvuran belirteci.</span><span class="sxs-lookup"><span data-stu-id="2f6e4-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f6e4-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f6e4-107">Requirements</span></span>  
 <span data-ttu-id="2f6e4-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f6e4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f6e4-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f6e4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f6e4-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f6e4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f6e4-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f6e4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
