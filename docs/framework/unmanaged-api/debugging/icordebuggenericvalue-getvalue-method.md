---
title: ICorDebugGenericValue::GetValue Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGenericValue.GetValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2432d79c6f17c7374d2beb400e93ae4088a8b1ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="44f2e-102">ICorDebugGenericValue::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="44f2e-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="44f2e-103">Bu genel değeri belirtilen arabelleğe kopyalar.</span><span class="sxs-lookup"><span data-stu-id="44f2e-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44f2e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44f2e-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44f2e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="44f2e-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="44f2e-106">[out] Bu Icordebuggenericvalue nesnesi tarafından temsil edilen değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="44f2e-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="44f2e-107">Değer, basit bir tür veya bir başvuru türü (diğer bir deyişle, bir işaretçi) olabilir.</span><span class="sxs-lookup"><span data-stu-id="44f2e-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44f2e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44f2e-108">Requirements</span></span>  
 <span data-ttu-id="44f2e-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44f2e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44f2e-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44f2e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44f2e-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44f2e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44f2e-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44f2e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
