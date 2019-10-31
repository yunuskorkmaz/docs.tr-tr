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
ms.openlocfilehash: 6964c931307a40f384ad8a8e355cab0aad575ec6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125768"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="05d50-102">ICorDebugClass::GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="05d50-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="05d50-103">Bu sınıfın tanımına başvuran `TypeDef` meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="05d50-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05d50-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05d50-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05d50-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05d50-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="05d50-106">dışı Bu sınıfın tanımına başvuran `mdTypeDef` belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="05d50-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05d50-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05d50-107">Requirements</span></span>  
 <span data-ttu-id="05d50-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05d50-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05d50-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="05d50-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05d50-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="05d50-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05d50-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05d50-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05d50-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05d50-112">See also</span></span>

- [<span data-ttu-id="05d50-113">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="05d50-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
