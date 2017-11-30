---
title: "ICorDebugCode::IsIL Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.IsIL
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 07b0490e322c70763a37b86fbb02e2f8b99bd768
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="102b6-102">ICorDebugCode::IsIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="102b6-102">ICorDebugCode::IsIL Method</span></span>
<span data-ttu-id="102b6-103">Bu "Icordebugcode" Microsoft Ara dili (MSIL) derlenmiş kod temsil edip etmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="102b6-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="102b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="102b6-104">Syntax</span></span>  
  
```  
HRESULT IsIL (  
    [out] BOOL       *pbIL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="102b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="102b6-105">Parameters</span></span>  
 `pbIL`  
 <span data-ttu-id="102b6-106">[out] `true` bu `ICorDebugCode` MSIL derlenmiş; Aksi takdirde kodunu temsil eder `false`.</span><span class="sxs-lookup"><span data-stu-id="102b6-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="102b6-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="102b6-107">Requirements</span></span>  
 <span data-ttu-id="102b6-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="102b6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="102b6-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="102b6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="102b6-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="102b6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="102b6-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="102b6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="102b6-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="102b6-112">See Also</span></span>  
 
