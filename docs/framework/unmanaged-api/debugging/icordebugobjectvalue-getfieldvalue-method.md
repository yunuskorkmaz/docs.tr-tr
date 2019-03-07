---
title: ICorDebugObjectValue::GetFieldValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d4e4a2dd9d1f419c94152e4131997f39b2d3b83
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493875"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="50a47-102">ICorDebugObjectValue::GetFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50a47-102">ICorDebugObjectValue::GetFieldValue Method</span></span>
<span data-ttu-id="50a47-103">Bu nesne değeri için belirtilen sınıf belirtilen alanının değerini alır.</span><span class="sxs-lookup"><span data-stu-id="50a47-103">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50a47-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50a47-104">Syntax</span></span>  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50a47-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50a47-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="50a47-106">[in] Alan değeri alınacağı bir sınıfı temsil eden bir "ICorDebugClass" nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="50a47-106">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="50a47-107">[in] Bir `mdFieldDef` başvuran alanı tanımlayan meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="50a47-107">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="50a47-108">[out] Belirtilen alanın değerini temsil eden bir "ICorDebugValue" nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="50a47-108">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50a47-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50a47-109">Remarks</span></span>  
 <span data-ttu-id="50a47-110">Belirtilen sınıfın `pClass` parametresi, nesne değerinin sınıfının hiyerarşisinde olmalıdır ve söz konusu sınıfın bir alan alan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="50a47-110">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="50a47-111">`GetFieldValue` Yöntemi yine de başarılı olur genel nesneleri ve Genel sınıflar için.</span><span class="sxs-lookup"><span data-stu-id="50a47-111">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="50a47-112">Örneğin, varsa MyDictionary\<V > sözlükten devralan\<dize, V >, ve nesne değeri MyDictionary türünde\<Int32 >, geçen `ICorDebugClass` sözlük nesnesi\<K, V > olur sözlüğün bir alan başarıyla alma\<string, Int32 >.</span><span class="sxs-lookup"><span data-stu-id="50a47-112">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50a47-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50a47-113">Requirements</span></span>  
 <span data-ttu-id="50a47-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50a47-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50a47-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50a47-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50a47-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50a47-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50a47-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50a47-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50a47-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50a47-118">See also</span></span>


