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
ms.openlocfilehash: 20315dfc426b63f2d526f3481756e165b388b41e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137604"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="80f49-102">ICorDebugEval2::CreateValueForType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80f49-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="80f49-103">Belirtilen türdeki yeni bir ICorDebugValue değeri, sıfır veya null değeri olan bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="80f49-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80f49-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80f49-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80f49-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80f49-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="80f49-106">'ndaki Türü temsil eden ICorDebugType nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="80f49-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="80f49-107">dışı Değeri temsil eden bir `ICorDebugValue` nesnesinin adresine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="80f49-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80f49-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80f49-108">Remarks</span></span>  
 <span data-ttu-id="80f49-109">`CreateValueForType`, `List<int>`gibi oluşturulmuş türler de dahil olmak üzere, rastgele bir nesne türü belirtmenize izin vererek [ıcorınkıt Geval:: CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) öğesini genelleştirir.</span><span class="sxs-lookup"><span data-stu-id="80f49-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="80f49-110">Bu yöntemin tek amacı, bir işlev değerlendirmesine geçirilebilecek bir değer üretmesidir.</span><span class="sxs-lookup"><span data-stu-id="80f49-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="80f49-111">Tür bir sınıf veya değer türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="80f49-111">The type must be a class or a value type.</span></span> <span data-ttu-id="80f49-112">Dizi değerleri veya dize değerleri oluşturmak için bu yöntemi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="80f49-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80f49-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80f49-113">Requirements</span></span>  
 <span data-ttu-id="80f49-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80f49-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80f49-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="80f49-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80f49-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="80f49-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80f49-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80f49-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
