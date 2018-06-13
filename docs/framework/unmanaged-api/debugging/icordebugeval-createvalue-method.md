---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d67784daee055106f104d74d098b9926c6de2ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417118"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="837b7-102">ICorDebugEval::CreateValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="837b7-102">ICorDebugEval::CreateValue Method</span></span>
<span data-ttu-id="837b7-103">Belirtilen türde bir değer sıfır ya da null bir başlangıç değeriyle birlikte oluşturur.</span><span class="sxs-lookup"><span data-stu-id="837b7-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="837b7-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="837b7-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="837b7-105">Kullanım [Icordebugeval2::createvaluefortype](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="837b7-105">Use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="837b7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="837b7-106">Syntax</span></span>  
  
```  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="837b7-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="837b7-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="837b7-108">[in] Değerini [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) numaralandırma değeri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="837b7-108">[in] A value of the [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="837b7-109">[in] İşaretçi bir [Icordebugclass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) değer sınıfının türü basit tür değilse belirten nesne.</span><span class="sxs-lookup"><span data-stu-id="837b7-109">[in] Pointer to an [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="837b7-110">[out] İşaretçi adresine "ICorDebugValue" nesnenin değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="837b7-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="837b7-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="837b7-111">Remarks</span></span>  
 <span data-ttu-id="837b7-112">`CreateValue` oluşturur bir `ICorDebugValue` bir işlev değerlendirmesi kullanmanın tek amacı için belirli türde nesne.</span><span class="sxs-lookup"><span data-stu-id="837b7-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="837b7-113">Bu değer nesnesi kullanıcı sabitleri parametre olarak geçirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="837b7-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="837b7-114">Değerin türü basit tür ilk değeri sıfır ise, veya null.</span><span class="sxs-lookup"><span data-stu-id="837b7-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="837b7-115">Kullanım [Icordebuggenericvalue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) basit tür değeri ayarlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="837b7-115">Use [ICorDebugGenericValue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="837b7-116">Varsa değerini `elementType` ELEMENT_TYPE_CLASS, olan bir "Icordebugreferencevalue" Al (döndürülen `ppValue`) null Nesne başvurusu temsil eden.</span><span class="sxs-lookup"><span data-stu-id="837b7-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="837b7-117">Nesne başvurusu parametrelerine sahip İşlev değerlendirmesi için null geçirmek için bu nesneyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="837b7-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="837b7-118">Ayarlayamazsınız `ICorDebugValue` şey; her zaman null kalır.</span><span class="sxs-lookup"><span data-stu-id="837b7-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="837b7-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="837b7-119">Requirements</span></span>  
 <span data-ttu-id="837b7-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="837b7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="837b7-121">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="837b7-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="837b7-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="837b7-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="837b7-123">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="837b7-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="837b7-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="837b7-124">See Also</span></span>  
    
 [<span data-ttu-id="837b7-125">CreateValueForType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="837b7-125">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)  
 <span data-ttu-id="837b7-126">Icordebugvalue</span><span class="sxs-lookup"><span data-stu-id="837b7-126">ICorDebugValue</span></span>
