---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16cf17d43fcad3c4f7a710678bbdc056f840eaca
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736812"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="f5d6d-102">ICorDebugType::EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5d6d-102">ICorDebugType::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="f5d6d-103">Bir arabirim işaretçisi alır içeren bir Icordebugtypeenum <xref:System.Type> bu Icordebugtype tarafından başvurulan sınıfın parametreleri.</span><span class="sxs-lookup"><span data-stu-id="f5d6d-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5d6d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5d6d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5d6d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5d6d-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="f5d6d-106">[out] Adresine bir işaretçi bir `ICorDebugTypeEnum` tür parametreleri içeren.</span><span class="sxs-lookup"><span data-stu-id="f5d6d-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5d6d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5d6d-107">Remarks</span></span>  
 <span data-ttu-id="f5d6d-108">Kullanabileceğiniz `EnumerateTypeParameters` CorElementType değeri tarafından döndürdüyse [Icordebugtype::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ve ELEMENT_TYPE_ PTR veya ELEMENT_TYPE_FNPTR.</span><span class="sxs-lookup"><span data-stu-id="f5d6d-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="f5d6d-109">Parametreler ve bunların sırası sayısını türüne bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="f5d6d-109">The number of parameters and their order depends on the type:</span></span>  
  
- <span data-ttu-id="f5d6d-110">ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE: Bulunan tür parametreleri sayısı `ICorDebugTypeEnum` bu yöntem döndürdüğünü, karşılık gelen sınıf için biçimsel tür parametrelerinin sayısına bağımlı.</span><span class="sxs-lookup"><span data-stu-id="f5d6d-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="f5d6d-111">Örneğin, türü ise `class Dict<String,int32>`, ardından `EnumerateTypeParameters` döndürür bir `ICorDebugTypeEnum` temsil eden nesneler içeren `String` ve `int32` dizideki.</span><span class="sxs-lookup"><span data-stu-id="f5d6d-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
- <span data-ttu-id="f5d6d-112">ELEMENT_TYPE_FNPTR: Bulunan tür parametreleri sayısı `ICorDebugTypeEnum` bir bağımsız değişken işlev tarafından kabul sayısından daha büyük olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f5d6d-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="f5d6d-113">Bulunan ilk tür parametresi `ICorDebugTypeEnum` işlevin dönüş türü ve sonraki tür parametreleri, işlevin parametrelerdir.</span><span class="sxs-lookup"><span data-stu-id="f5d6d-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
- <span data-ttu-id="f5d6d-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF veya ELEMENT_TYPE_PTR: Bir tür parametresi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f5d6d-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="f5d6d-115">Örneğin, türü gibi bir dizi türü ise `int32[]`,`EnumerateTypeParameters` döndüreceği bir `ICorDebugTypeEnum` içeren bir nesneyi temsil eden `int32`.</span><span class="sxs-lookup"><span data-stu-id="f5d6d-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5d6d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5d6d-116">Requirements</span></span>  
 <span data-ttu-id="f5d6d-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5d6d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5d6d-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5d6d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5d6d-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5d6d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5d6d-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5d6d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
