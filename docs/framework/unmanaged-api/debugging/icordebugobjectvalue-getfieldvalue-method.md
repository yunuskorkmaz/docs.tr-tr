---
title: ICorDebugObjectValue::GetFieldValue Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue.GetFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33c3f368d9b78b899f54c989427ea1f660346487
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="20313-102">ICorDebugObjectValue::GetFieldValue Metodu</span><span class="sxs-lookup"><span data-stu-id="20313-102">ICorDebugObjectValue::GetFieldValue Method</span></span>
<span data-ttu-id="20313-103">Bu nesne değeri için belirtilen sınıf belirtilen alanının değerini alır.</span><span class="sxs-lookup"><span data-stu-id="20313-103">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20313-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20313-104">Syntax</span></span>  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20313-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20313-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="20313-106">[in] Bir işaretçi "ICorDebugClass" nesneye için alan değeri almak istediğiniz sınıfı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="20313-106">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="20313-107">[in] Bir `mdFieldDef` alan açıklayan meta veriler başvuran belirteci.</span><span class="sxs-lookup"><span data-stu-id="20313-107">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="20313-108">[out] Belirtilen alanın değerini temsil eden bir "ICorDebugValue" nesnesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="20313-108">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20313-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20313-109">Remarks</span></span>  
 <span data-ttu-id="20313-110">Belirtilen sınıf `pClass` parametresi, nesne değerinin sınıfının hiyerarşisinde olmalıdır ve alan bu sınıfın bir alan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20313-110">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="20313-111">`GetFieldValue` Yöntemi yine de başarılı genel nesneler ve Genel sınıflar için.</span><span class="sxs-lookup"><span data-stu-id="20313-111">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="20313-112">Örneğin, varsa MyDictionary\<V > sözlükten devralır\<dize, V >, ve nesne değeri türü MyDictionary\<Int32 >, geçen `ICorDebugClass` sözlük nesnesi\<K, V > olur başarıyla sözlük alanı almak\<dize, Int32 >.</span><span class="sxs-lookup"><span data-stu-id="20313-112">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20313-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20313-113">Requirements</span></span>  
 <span data-ttu-id="20313-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20313-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20313-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20313-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20313-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20313-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20313-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20313-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20313-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20313-118">See Also</span></span>  
    
 
