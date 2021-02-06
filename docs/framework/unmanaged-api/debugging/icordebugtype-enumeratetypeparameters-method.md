---
description: ': ICorDebugType:: EnumerateTypeParameters yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugType::EnumerateTypeParameters Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
ms.openlocfilehash: 5189394cbb39cd133ebce494107f4ca65660bb5b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658418"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="bfa57-103">ICorDebugType::EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfa57-103">ICorDebugType::EnumerateTypeParameters Method</span></span>

<span data-ttu-id="bfa57-104"><xref:System.Type>Bu ICorDebugType tarafından başvurulan sınıfın parametrelerini Içeren ICorDebugTypeEnum için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="bfa57-104">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfa57-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfa57-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfa57-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bfa57-106">Parameters</span></span>  

 `ppTyParEnum`  
 <span data-ttu-id="bfa57-107">dışı `ICorDebugTypeEnum` Türünün parametrelerini içeren adresinin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="bfa57-107">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfa57-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bfa57-108">Remarks</span></span>  

 <span data-ttu-id="bfa57-109">`EnumerateTypeParameters` [ICorDebugType:: GetType](icordebugtype-gettype-method.md) tarafından döndürülen CorElementType değeri element_type_class, element_type_valuetype, element_type_array, element_type_szarray, element_type_byref, ELEMENT_TYPE_PTR veya element_type_fnptr ise kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bfa57-109">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="bfa57-110">Parametrelerin sayısı ve sırası türüne bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="bfa57-110">The number of parameters and their order depends on the type:</span></span>  
  
- <span data-ttu-id="bfa57-111">ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE: Bu yöntemin döndürdüğü ' de bulunan tür parametrelerinin sayısı `ICorDebugTypeEnum` , karşılık gelen sınıf için biçimsel tür parametrelerinin sayısına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bfa57-111">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="bfa57-112">Örneğin, türü ise `class Dict<String,int32>` , `EnumerateTypeParameters` `ICorDebugTypeEnum` ve sırasını temsil eden nesneleri içeren bir döndürür `String` `int32` .</span><span class="sxs-lookup"><span data-stu-id="bfa57-112">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
- <span data-ttu-id="bfa57-113">ELEMENT_TYPE_FNPTR: içinde yer alan tür parametrelerinin sayısı, `ICorDebugTypeEnum` işlev tarafından kabul edilen bağımsız değişken sayısından bir büyük olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bfa57-113">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="bfa57-114">İçinde yer alan ilk tür parametresi, `ICorDebugTypeEnum` işlevin dönüş türüdür ve sonraki tür parametreleri işlevin parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="bfa57-114">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
- <span data-ttu-id="bfa57-115">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF veya ELEMENT_TYPE_PTR: bir tür parametresi döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="bfa57-115">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="bfa57-116">Örneğin, türü gibi bir dizi türü ise `int32[]` , `EnumerateTypeParameters` `ICorDebugTypeEnum` temsil eden nesneyi içeren bir nesnesi döndürür `int32` .</span><span class="sxs-lookup"><span data-stu-id="bfa57-116">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfa57-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bfa57-117">Requirements</span></span>  

 <span data-ttu-id="bfa57-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfa57-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfa57-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bfa57-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bfa57-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bfa57-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfa57-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfa57-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
