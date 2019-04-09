---
title: ICorDebugClass::GetToken Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetToken
helpviewer_keywords:
- GetToken method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetToken method [.NET Framework debugging]
ms.assetid: ee5c848a-eac4-4462-b07a-07ccd76a75df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4f33bb15a351be5fe8318dcc3339d429dec039e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183709"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="7470d-102">ICorDebugClass::GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="7470d-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="7470d-103">Alır `TypeDef` başvuran tanım bu sınıfın meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="7470d-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7470d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7470d-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7470d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7470d-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="7470d-106">[out] Bir işaretçi bir `mdTypeDef` başvuran tanım bu sınıfın belirteci.</span><span class="sxs-lookup"><span data-stu-id="7470d-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7470d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7470d-107">Requirements</span></span>  
 <span data-ttu-id="7470d-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7470d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7470d-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7470d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7470d-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7470d-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7470d-111">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="7470d-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7470d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7470d-112">See also</span></span>

- [<span data-ttu-id="7470d-113">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7470d-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
