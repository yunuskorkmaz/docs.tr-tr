---
title: ICorDebugType::GetType Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d881a1fe3965b6e1d89e6172c887061434cd52ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418724"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="21cb3-102">ICorDebugType::GetType Metodu</span><span class="sxs-lookup"><span data-stu-id="21cb3-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="21cb3-103">Ortak dil çalışma zamanı (CLR) yerel türünü tanımlayan bir CorElementType değeri alır <xref:System.Type> bu Icordebugtype tarafından temsil edilen.</span><span class="sxs-lookup"><span data-stu-id="21cb3-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21cb3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21cb3-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21cb3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21cb3-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="21cb3-106">[out] Değerini gösteren bir işaretçi `CorElementType` CLR belirten numaralandırma <xref:System.Type> bu `ICorDebugType` temsil eder.</span><span class="sxs-lookup"><span data-stu-id="21cb3-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21cb3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21cb3-107">Remarks</span></span>  
 <span data-ttu-id="21cb3-108">Varsa değerini `ty` ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE, [Icordebugtype::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) yöntemi için genel bir tür dizilerine türünü almak için çağrılabilir; Aksi takdirde çağırmayın `ICorDebugType::GetClass`.</span><span class="sxs-lookup"><span data-stu-id="21cb3-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21cb3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21cb3-109">Requirements</span></span>  
 <span data-ttu-id="21cb3-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21cb3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21cb3-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21cb3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21cb3-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21cb3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21cb3-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21cb3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
