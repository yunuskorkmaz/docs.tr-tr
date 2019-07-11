---
title: ICorDebugType::GetClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd68df77adafb8b21e7684b28fe978722ca37e16
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736796"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="6c2ec-102">ICorDebugType::GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c2ec-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="6c2ec-103">Örneklenmemiş genel türü temsil eden bir Icordebugclass bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c2ec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c2ec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c2ec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c2ec-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="6c2ec-106">[out] Adresine bir işaretçi bir `ICorDebugClass` örneklenmemiş genel türü temsil eden arabirim.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c2ec-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c2ec-107">Remarks</span></span>  
 <span data-ttu-id="6c2ec-108">`GetClass` yalnızca belirli koşullar altında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="6c2ec-109">Çağrı [Icordebugtype::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) çağırmadan önce `GetClass`.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-109">Call [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="6c2ec-110">Varsa `ICorDebugType::GetType` ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE, bir CorElementType değeri döndürür `GetClass` örneklenmemiş türü için genel bir tür almak için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c2ec-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c2ec-111">Requirements</span></span>  
 <span data-ttu-id="6c2ec-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c2ec-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c2ec-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c2ec-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c2ec-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c2ec-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c2ec-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c2ec-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
