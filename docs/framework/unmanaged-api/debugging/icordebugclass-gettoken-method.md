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
ms.openlocfilehash: 59f450117d1a52ce7b900d9d67330fc98281afa0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728426"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="104ae-102">ICorDebugClass::GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="104ae-102">ICorDebugClass::GetToken Method</span></span>

<span data-ttu-id="104ae-103">`TypeDef`Bu sınıfın tanımına başvuran meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="104ae-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="104ae-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="104ae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="104ae-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="104ae-105">Parameters</span></span>  

 `pTypeDef`  
 <span data-ttu-id="104ae-106">dışı `mdTypeDef` Bu sınıfın tanımına başvuran bir belirteç işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="104ae-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="104ae-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="104ae-107">Requirements</span></span>  

 <span data-ttu-id="104ae-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="104ae-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="104ae-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="104ae-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="104ae-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="104ae-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="104ae-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="104ae-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="104ae-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="104ae-112">See also</span></span>

- [<span data-ttu-id="104ae-113">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="104ae-113">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)
