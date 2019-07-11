---
title: ICorDebugEval2::CreateValueForType Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ffddb8242b6627239a99bd9223b98762910b831
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753242"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="5e293-102">ICorDebugEval2::CreateValueForType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e293-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="5e293-103">Bir işaretçi için yeni bir Icordebugvalue belirtilen türe ait bir başlangıç değeri sıfır ya da null ile alır.</span><span class="sxs-lookup"><span data-stu-id="5e293-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e293-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e293-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e293-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e293-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="5e293-106">[in] İşaretçi Icordebugtype nesnenin türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5e293-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="5e293-107">[out] İşaretçi adresine bir `ICorDebugValue` değerini temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="5e293-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e293-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e293-108">Remarks</span></span>  
 <span data-ttu-id="5e293-109">`CreateValueForType` genelleştirir [Icordebugeval::createvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) rasgele nesne türünü belirtmenize olanak tanıyarak dahil olmak üzere oluşturulmuş türleri gibi `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="5e293-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="5e293-110">Bu yöntemin tek amacı, bir işlev değerlendirmesi için geçirilen değer oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="5e293-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="5e293-111">Türü, bir sınıf veya değer türü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e293-111">The type must be a class or a value type.</span></span> <span data-ttu-id="5e293-112">Bu yöntem, değerler dizisi veya dize değerleri oluşturmak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="5e293-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e293-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e293-113">Requirements</span></span>  
 <span data-ttu-id="5e293-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e293-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e293-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e293-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e293-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e293-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e293-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e293-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
