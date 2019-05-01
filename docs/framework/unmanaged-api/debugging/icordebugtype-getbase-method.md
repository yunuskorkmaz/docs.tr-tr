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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d04bc67013a2227f295ac3a41be027b9f9b04e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946321"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="c0cae-102">ICorDebugType::GetBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0cae-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="c0cae-103">Bu tarafından temsil edilen türü varsa temel türünü temsil eden bir Icordebugtype için bir arabirim işaretçisi alır `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="c0cae-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0cae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0cae-104">Syntax</span></span>  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0cae-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0cae-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="c0cae-106">[out] Adresine bir işaretçi bir `ICorDebugType` taban türünü temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="c0cae-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0cae-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0cae-107">Remarks</span></span>  
 <span data-ttu-id="c0cae-108">Bir tür için temel tür bakarak, tüm alanları bir nesnenin ya da üst yazdırma gibi yaygın hata ayıklayıcı işlevselliği uygulamak kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="c0cae-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0cae-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0cae-109">Requirements</span></span>  
 <span data-ttu-id="c0cae-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0cae-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0cae-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0cae-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0cae-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0cae-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0cae-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0cae-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
