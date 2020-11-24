---
title: ICorDebugType::GetBase Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
ms.openlocfilehash: 967f8f25e240f484ae86852c740be12cd3a6409e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681827"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="59376-102">ICorDebugType::GetBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59376-102">ICorDebugType::GetBase Method</span></span>

<span data-ttu-id="59376-103">Bir ICorDebugType öğesine, varsa, bu tür tarafından temsil edilen türün temel türünü temsil eden bir arabirim işaretçisi alır `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="59376-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59376-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="59376-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59376-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="59376-105">Parameters</span></span>  

 `pBase`  
 <span data-ttu-id="59376-106">dışı `ICorDebugType` Temel türü temsil eden nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="59376-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59376-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59376-107">Remarks</span></span>  

 <span data-ttu-id="59376-108">Bir türün temel türünü aramak, bir nesnenin veya onun üst sınıflarının tüm alanlarını yazdırmak gibi yaygın hata ayıklayıcı işlevselliği uygulamak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="59376-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59376-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59376-109">Requirements</span></span>  

 <span data-ttu-id="59376-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59376-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59376-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="59376-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59376-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="59376-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59376-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59376-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
