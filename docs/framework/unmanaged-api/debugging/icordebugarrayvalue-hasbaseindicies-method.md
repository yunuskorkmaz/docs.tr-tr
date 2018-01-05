---
title: "ICorDebugArrayValue::HasBaseIndicies Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.HasBaseIndicies
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1aa7e263c4e6b1460e327869c0c6945cba65328
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="53bcf-102">ICorDebugArrayValue::HasBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53bcf-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="53bcf-103">Tüm boyutlar bu dizinin sıfır olmayan temel bir dizine sahip olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="53bcf-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53bcf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53bcf-104">Syntax</span></span>  
  
```  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53bcf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="53bcf-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="53bcf-106">[out] Boolean bir değer için bir işaretçi `true` , bir veya daha fazla boyutları bu `ICorDebugArrayValue` nesnesine sahip sıfır olmayan temel bir dizin; Aksi halde, Boolean değeri `false`.</span><span class="sxs-lookup"><span data-stu-id="53bcf-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53bcf-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53bcf-107">Requirements</span></span>  
 <span data-ttu-id="53bcf-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53bcf-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53bcf-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53bcf-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53bcf-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53bcf-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53bcf-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53bcf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
