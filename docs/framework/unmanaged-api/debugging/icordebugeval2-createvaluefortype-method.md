---
title: "ICorDebugEval2::CreateValueForType Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 18e7eb5fc30c27fd2c4865dc61e2f75dc9e96068
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="bf70f-102">ICorDebugEval2::CreateValueForType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bf70f-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="bf70f-103">Bir işaretçi belirtilen türe ait yeni Icordebugvalue için sıfır ya da null bir başlangıç değeriyle birlikte alır.</span><span class="sxs-lookup"><span data-stu-id="bf70f-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf70f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf70f-104">Syntax</span></span>  
  
```  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf70f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bf70f-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="bf70f-106">[in] İşaretçi Icordebugtype nesneye türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bf70f-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="bf70f-107">[out] İşaretçi adresine bir `ICorDebugValue` değerini temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="bf70f-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf70f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf70f-108">Remarks</span></span>  
 <span data-ttu-id="bf70f-109">`CreateValueForType`genelleştirir [Icordebugeval::createvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) rasgele nesne türünü belirtmenize olanak tanıyarak dahil olmak üzere oluşturulan türleri gibi `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="bf70f-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="bf70f-110">Tek amacı, bu yöntem, bir işlev değerlendirmesi için geçirilen değer oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="bf70f-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="bf70f-111">Türün bir sınıf veya bir değer türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf70f-111">The type must be a class or a value type.</span></span> <span data-ttu-id="bf70f-112">Bu yöntem, dizi değerlerini veya dize değerlerini oluşturmak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="bf70f-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf70f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf70f-113">Requirements</span></span>  
 <span data-ttu-id="bf70f-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf70f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf70f-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf70f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf70f-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf70f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf70f-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf70f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
