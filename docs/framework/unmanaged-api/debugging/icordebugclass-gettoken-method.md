---
title: ICorDebugClass::GetToken Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass.GetToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass::GetToken
helpviewer_keywords:
- GetToken method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetToken method [.NET Framework debugging]
ms.assetid: ee5c848a-eac4-4462-b07a-07ccd76a75df
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 805ecd7111fd06dfe0d13f60e6dd1e64ec3c37b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="c83c8-102">ICorDebugClass::GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="c83c8-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="c83c8-103">Alır `TypeDef` Bu sınıf tanımına başvurur meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="c83c8-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c83c8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c83c8-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c83c8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c83c8-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="c83c8-106">[out] Bir işaretçi bir `mdTypeDef` Bu sınıf tanımına başvurur belirteci.</span><span class="sxs-lookup"><span data-stu-id="c83c8-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c83c8-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c83c8-107">Requirements</span></span>  
 <span data-ttu-id="c83c8-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c83c8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c83c8-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c83c8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c83c8-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c83c8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c83c8-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c83c8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c83c8-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c83c8-112">See Also</span></span>  
 [<span data-ttu-id="c83c8-113">Meta veri arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c83c8-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
