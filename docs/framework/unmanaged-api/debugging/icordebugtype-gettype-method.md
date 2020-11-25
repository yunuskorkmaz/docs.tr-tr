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
ms.openlocfilehash: f0f45d5f0b2ea8cefa6bd36e909ae43d80c968ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700892"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="07305-102">ICorDebugType::GetType Metodu</span><span class="sxs-lookup"><span data-stu-id="07305-102">ICorDebugType::GetType Method</span></span>

<span data-ttu-id="07305-103">Bu ICorDebugType tarafından temsil edilen ortak dil çalışma zamanının (CLR) yerel türünü açıklayan bir CorElementType değeri alır <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="07305-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07305-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="07305-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07305-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07305-105">Parameters</span></span>  

 `ty`  
 <span data-ttu-id="07305-106">dışı `CorElementType` Numaralandırmadaki, bu temsil eden clr 'yi gösteren bir değer işaretçisi <xref:System.Type> `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="07305-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07305-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07305-107">Remarks</span></span>  

 <span data-ttu-id="07305-108">Değeri `ty` element_type_class ya da element_type_valuetype ise, [ICorDebugType:: GetClass](icordebugtype-getclass-method.md) yöntemi, genel bir türün örneklenmemiş türünü almak için çağrılabilir; Aksi takdirde, çağırmayın `ICorDebugType::GetClass` .</span><span class="sxs-lookup"><span data-stu-id="07305-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07305-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07305-109">Requirements</span></span>  

 <span data-ttu-id="07305-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07305-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07305-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="07305-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07305-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="07305-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07305-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07305-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
