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
ms.openlocfilehash: c24d6e9c42a091eafbe6d4bdee2bb4e055fd8852
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772039"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="e1824-102">ICorDebugType::GetBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1824-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="e1824-103">Bu tarafından temsil edilen türü varsa temel türünü temsil eden bir Icordebugtype için bir arabirim işaretçisi alır `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="e1824-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1824-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1824-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1824-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1824-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="e1824-106">[out] Adresine bir işaretçi bir `ICorDebugType` taban türünü temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="e1824-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1824-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1824-107">Remarks</span></span>  
 <span data-ttu-id="e1824-108">Bir tür için temel tür bakarak, tüm alanları bir nesnenin ya da üst yazdırma gibi yaygın hata ayıklayıcı işlevselliği uygulamak kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e1824-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1824-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1824-109">Requirements</span></span>  
 <span data-ttu-id="e1824-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1824-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1824-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1824-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1824-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1824-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1824-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1824-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
