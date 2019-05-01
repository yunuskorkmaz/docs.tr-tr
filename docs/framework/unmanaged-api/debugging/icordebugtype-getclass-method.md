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
ms.openlocfilehash: 0915027ce6a3768ff854eafc5496c5057081cc4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946217"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="e8fde-102">ICorDebugType::GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e8fde-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="e8fde-103">Örneklenmemiş genel türü temsil eden bir Icordebugclass bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="e8fde-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8fde-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8fde-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8fde-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e8fde-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="e8fde-106">[out] Adresine bir işaretçi bir `ICorDebugClass` örneklenmemiş genel türü temsil eden arabirim.</span><span class="sxs-lookup"><span data-stu-id="e8fde-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8fde-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8fde-107">Remarks</span></span>  
 <span data-ttu-id="e8fde-108">`GetClass` yalnızca belirli koşullar altında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8fde-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="e8fde-109">Çağrı [Icordebugtype::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) çağırmadan önce `GetClass`.</span><span class="sxs-lookup"><span data-stu-id="e8fde-109">Call [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="e8fde-110">Varsa `ICorDebugType::GetType` ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE, bir CorElementType değeri döndürür `GetClass` örneklenmemiş türü için genel bir tür almak için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8fde-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8fde-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8fde-111">Requirements</span></span>  
 <span data-ttu-id="e8fde-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8fde-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8fde-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8fde-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8fde-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8fde-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8fde-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8fde-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
