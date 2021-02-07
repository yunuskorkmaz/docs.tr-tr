---
description: ': ICorDebugObjectValue:: GetFieldValue metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 38dac36747b286ab16ae3310b6b59695480a6ff1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722197"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="6a785-103">ICorDebugObjectValue::GetFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a785-103">ICorDebugObjectValue::GetFieldValue Method</span></span>

<span data-ttu-id="6a785-104">Bu nesne değeri için belirtilen sınıftaki belirtilen alanın değerini alır.</span><span class="sxs-lookup"><span data-stu-id="6a785-104">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a785-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a785-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a785-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a785-106">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="6a785-107">'ndaki Alan değerinin alınacağı sınıfı temsil eden bir "ICorDebugClass" nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6a785-107">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="6a785-108">'ndaki `mdFieldDef` Alanı tanımlayan meta verilere başvuruda bulunan bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="6a785-108">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="6a785-109">dışı Belirtilen alanın değerini temsil eden bir "ICorDebugValue" nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6a785-109">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a785-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a785-110">Remarks</span></span>  

 <span data-ttu-id="6a785-111">Parametresinde belirtilen sınıf, `pClass` nesne değerinin sınıfının hiyerarşisinde olmalıdır ve alan bu sınıfın bir alanı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a785-111">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="6a785-112">`GetFieldValue`Genel nesneler ve genel sınıflar için yöntem yine de başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="6a785-112">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="6a785-113">Örneğin, MyDictionary \<V> sözlükten devralırsa \<string,V> ve nesne değeri MyDictionary türünde Ise \<int32> , `ICorDebugClass` Sözlük nesnesini \<K,V> başarılı bir şekilde sözlük alanı alır \<string,int32> .</span><span class="sxs-lookup"><span data-stu-id="6a785-113">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a785-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a785-114">Requirements</span></span>  

 <span data-ttu-id="6a785-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a785-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a785-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6a785-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a785-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6a785-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a785-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a785-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a785-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a785-119">See also</span></span>
