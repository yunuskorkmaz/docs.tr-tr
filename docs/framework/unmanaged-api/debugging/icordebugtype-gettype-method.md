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
ms.openlocfilehash: f6b36c524921a4fecf8bc5ddcbace62af6450b6d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492432"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="34c0b-102">ICorDebugType::GetType Metodu</span><span class="sxs-lookup"><span data-stu-id="34c0b-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="34c0b-103">Ortak dil çalışma zamanı (CLR) yerel türünü açıklayan bir CorElementType değerini alır <xref:System.Type> bu Icordebugtype tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="34c0b-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34c0b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34c0b-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34c0b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34c0b-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="34c0b-106">[out] Bir işaretçi değerini `CorElementType` CLR gösteren numaralandırma <xref:System.Type> bu `ICorDebugType` temsil eder.</span><span class="sxs-lookup"><span data-stu-id="34c0b-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34c0b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34c0b-107">Remarks</span></span>  
 <span data-ttu-id="34c0b-108">Varsa değerini `ty` ELEMENT_TYPE_CLASS ya da ELEMENT_TYPE_VALUETYPE, [Icordebugtype::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) yöntemi örneklenmemiş türü için genel bir tür almak için çağrılabilir; Aksi takdirde, çağırmayın `ICorDebugType::GetClass`.</span><span class="sxs-lookup"><span data-stu-id="34c0b-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34c0b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34c0b-109">Requirements</span></span>  
 <span data-ttu-id="34c0b-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34c0b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34c0b-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34c0b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34c0b-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34c0b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34c0b-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34c0b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
