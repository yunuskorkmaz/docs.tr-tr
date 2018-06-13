---
title: ICorDebugType::GetClass Metodu
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
ms.openlocfilehash: ff2258faa8bc766c8c769f4e135f868334516b96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422568"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="13084-102">ICorDebugType::GetClass Metodu</span><span class="sxs-lookup"><span data-stu-id="13084-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="13084-103">Arabirim işaretçisi dizilerine genel türünü temsil eden bir Icordebugclass alır.</span><span class="sxs-lookup"><span data-stu-id="13084-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13084-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13084-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13084-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13084-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="13084-106">[out] Adresine bir işaretçi bir `ICorDebugClass` dizilerine genel tür temsil eden arabirim.</span><span class="sxs-lookup"><span data-stu-id="13084-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13084-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13084-107">Remarks</span></span>  
 <span data-ttu-id="13084-108">`GetClass` yalnızca belirli koşullar altında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="13084-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="13084-109">Çağrı [Icordebugtype::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) çağırmadan önce `GetClass`.</span><span class="sxs-lookup"><span data-stu-id="13084-109">Call [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="13084-110">Varsa `ICorDebugType::GetType` ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE, CorElementType değeri döndürür `GetClass` için genel bir tür dizilerine türünü almak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="13084-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13084-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13084-111">Requirements</span></span>  
 <span data-ttu-id="13084-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13084-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13084-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13084-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13084-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13084-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13084-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13084-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
