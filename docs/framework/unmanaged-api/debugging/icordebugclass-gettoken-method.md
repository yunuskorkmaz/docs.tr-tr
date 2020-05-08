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
ms.openlocfilehash: 3433f5f69927afb501c2596571f138e3a69fabb6
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894120"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="144ba-102">ICorDebugClass::GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="144ba-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="144ba-103">Bu sınıfın `TypeDef` tanımına başvuran meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="144ba-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="144ba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="144ba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="144ba-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="144ba-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="144ba-106">dışı Bu sınıfın tanımına başvuran `mdTypeDef` bir belirteç işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="144ba-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="144ba-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="144ba-107">Requirements</span></span>  
 <span data-ttu-id="144ba-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="144ba-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="144ba-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="144ba-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="144ba-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="144ba-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="144ba-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="144ba-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="144ba-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="144ba-112">See also</span></span>

- [<span data-ttu-id="144ba-113">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="144ba-113">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)
