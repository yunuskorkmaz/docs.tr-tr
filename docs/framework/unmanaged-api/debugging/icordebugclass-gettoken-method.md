---
description: ': ICorDebugClass:: GetToken metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f87b71800410fc3a95790e6d35cf4bd10a5ce747
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711545"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="99be6-103">ICorDebugClass::GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="99be6-103">ICorDebugClass::GetToken Method</span></span>

<span data-ttu-id="99be6-104">`TypeDef`Bu sınıfın tanımına başvuran meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="99be6-104">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99be6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99be6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99be6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99be6-106">Parameters</span></span>  

 `pTypeDef`  
 <span data-ttu-id="99be6-107">dışı `mdTypeDef` Bu sınıfın tanımına başvuran bir belirteç işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="99be6-107">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99be6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99be6-108">Requirements</span></span>  

 <span data-ttu-id="99be6-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99be6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99be6-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="99be6-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99be6-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="99be6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99be6-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99be6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99be6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99be6-113">See also</span></span>

- [<span data-ttu-id="99be6-114">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="99be6-114">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)
