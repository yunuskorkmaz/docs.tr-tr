---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgeval:: CreateValue yöntemi'
title: ICorDebugEval::CreateValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
ms.openlocfilehash: f5ea753b5b95c68136e7b799aad88eee5845ea82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694168"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="05dc1-103">ICorDebugEval::CreateValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05dc1-103">ICorDebugEval::CreateValue Method</span></span>

<span data-ttu-id="05dc1-104">Sıfır veya null başlangıç değeri ile belirtilen türde bir değer oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05dc1-104">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="05dc1-105">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="05dc1-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="05dc1-106">Bunun yerine [ICorDebugEval2:: CreateValueForType](icordebugeval2-createvaluefortype-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="05dc1-106">Use [ICorDebugEval2::CreateValueForType](icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05dc1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05dc1-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05dc1-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05dc1-108">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="05dc1-109">'ndaki Değerin türünü belirten [CorElementType](../metadata/corelementtype-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="05dc1-109">[in] A value of the [CorElementType](../metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="05dc1-110">'ndaki Tür temel bir tür değilse, değerin sınıfını belirten [ICorDebugClass](icordebugclass-interface.md) nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="05dc1-110">[in] Pointer to an [ICorDebugClass](icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="05dc1-111">dışı Değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="05dc1-111">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05dc1-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05dc1-112">Remarks</span></span>  

 <span data-ttu-id="05dc1-113">`CreateValue``ICorDebugValue`tek bir işlev değerlendirmesinde kullanmak amacıyla verilen türde bir nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05dc1-113">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="05dc1-114">Bu değer nesnesi, Kullanıcı sabitlerini parametre olarak geçirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="05dc1-114">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="05dc1-115">Değerin türü temel bir tür ise, ilk değeri sıfır veya null olur.</span><span class="sxs-lookup"><span data-stu-id="05dc1-115">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="05dc1-116">Temel bir türün değerini ayarlamak için [ICorDebugGenericValue:: SetValue](icordebuggenericvalue-setvalue-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="05dc1-116">Use [ICorDebugGenericValue::SetValue](icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="05dc1-117">Değeri `elementType` element_type_class ise, `ppValue` null nesne başvurusunu temsil eden bir "ICorDebugReferenceValue" (içinde döndürülen) alırsınız.</span><span class="sxs-lookup"><span data-stu-id="05dc1-117">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="05dc1-118">Bu nesneyi, nesne başvuru parametrelerine sahip bir işlev değerlendirmesine null geçirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05dc1-118">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="05dc1-119">`ICorDebugValue`Her şeyi hiçbir şekilde ayarlayamazsınız; her zaman null kalır.</span><span class="sxs-lookup"><span data-stu-id="05dc1-119">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05dc1-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05dc1-120">Requirements</span></span>  

 <span data-ttu-id="05dc1-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05dc1-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05dc1-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="05dc1-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05dc1-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="05dc1-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05dc1-124">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="05dc1-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05dc1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05dc1-125">See also</span></span>

- [<span data-ttu-id="05dc1-126">CreateValueForType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05dc1-126">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)
- [<span data-ttu-id="05dc1-127">ICorDebugEval Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05dc1-127">ICorDebugEval Interface</span></span>](icordebugeval-interface.md)
