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
ms.openlocfilehash: 660bc13e8109994f59444c0adebbc97f54de0b43
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207588"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="88394-102">ICorDebugObjectValue::GetFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88394-102">ICorDebugObjectValue::GetFieldValue Method</span></span>
<span data-ttu-id="88394-103">Bu nesne değeri için belirtilen sınıftaki belirtilen alanın değerini alır.</span><span class="sxs-lookup"><span data-stu-id="88394-103">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88394-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88394-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88394-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88394-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="88394-106">'ndaki Alan değerinin alınacağı sınıfı temsil eden bir "ICorDebugClass" nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="88394-106">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="88394-107">'ndaki `mdFieldDef`Alanı tanımlayan meta verilere başvuruda bulunan bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="88394-107">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="88394-108">dışı Belirtilen alanın değerini temsil eden bir "ICorDebugValue" nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="88394-108">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88394-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88394-109">Remarks</span></span>  
 <span data-ttu-id="88394-110">Parametresinde belirtilen sınıf, `pClass` nesne değerinin sınıfının hiyerarşisinde olmalıdır ve alan bu sınıfın bir alanı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="88394-110">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="88394-111">`GetFieldValue`Genel nesneler ve genel sınıflar için yöntem yine de başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="88394-111">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="88394-112">Örneğin, MyDictionary \< v> sözlük \< dizesinden, v> ' den devralırsa ve nesne değeri mydictionary Int32> türünde Ise, \< `ICorDebugClass` sözlük \< K, r> sözlük dizesinin bir alanını başarıyla alır, \< Int32>.</span><span class="sxs-lookup"><span data-stu-id="88394-112">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88394-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88394-113">Requirements</span></span>  
 <span data-ttu-id="88394-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88394-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88394-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="88394-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88394-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="88394-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88394-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88394-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88394-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88394-118">See also</span></span>
