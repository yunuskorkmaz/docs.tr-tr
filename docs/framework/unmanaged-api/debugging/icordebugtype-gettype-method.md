---
description: ': ICorDebugType:: GetType yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 922791e51855badfb1fd548e08953a2f660f971a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658223"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="21281-103">ICorDebugType::GetType Metodu</span><span class="sxs-lookup"><span data-stu-id="21281-103">ICorDebugType::GetType Method</span></span>

<span data-ttu-id="21281-104">Bu ICorDebugType tarafından temsil edilen ortak dil çalışma zamanının (CLR) yerel türünü açıklayan bir CorElementType değeri alır <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="21281-104">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21281-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21281-105">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21281-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21281-106">Parameters</span></span>  

 `ty`  
 <span data-ttu-id="21281-107">dışı `CorElementType` Numaralandırmadaki, bu temsil eden clr 'yi gösteren bir değer işaretçisi <xref:System.Type> `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="21281-107">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21281-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21281-108">Remarks</span></span>  

 <span data-ttu-id="21281-109">Değeri `ty` element_type_class ya da element_type_valuetype ise, [ICorDebugType:: GetClass](icordebugtype-getclass-method.md) yöntemi, genel bir türün örneklenmemiş türünü almak için çağrılabilir; Aksi takdirde, çağırmayın `ICorDebugType::GetClass` .</span><span class="sxs-lookup"><span data-stu-id="21281-109">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21281-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21281-110">Requirements</span></span>  

 <span data-ttu-id="21281-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21281-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21281-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="21281-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21281-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="21281-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21281-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21281-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
