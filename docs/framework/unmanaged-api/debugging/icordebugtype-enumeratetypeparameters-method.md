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
ms.openlocfilehash: 57a82e4ec106fead105cc7f200e7e56026004328
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122375"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="d660f-102">ICorDebugType::EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d660f-102">ICorDebugType::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="d660f-103">Bu ICorDebugType tarafından başvurulan sınıfın <xref:System.Type> parametrelerini içeren bir ICorDebugTypeEnum için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="d660f-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d660f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d660f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d660f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d660f-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="d660f-106">dışı Türün parametrelerini içeren `ICorDebugTypeEnum` adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d660f-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d660f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d660f-107">Remarks</span></span>  
 <span data-ttu-id="d660f-108">[ICorDebugType:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) tarafından döndürülen CorElementType değeri element_type_class, element_type_valuetype, element_type_array, element_type_szarray, element_type_byref, ELEMENT_TYPE_PTR veya ELEMENT_TYPE_FNPTR ise `EnumerateTypeParameters` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d660f-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="d660f-109">Parametrelerin sayısı ve sırası türüne bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="d660f-109">The number of parameters and their order depends on the type:</span></span>  
  
- <span data-ttu-id="d660f-110">ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE: Bu yöntemin döndürdüğü `ICorDebugTypeEnum` içindeki tür parametrelerinin sayısı, karşılık gelen sınıf için biçimsel tür parametrelerinin sayısına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d660f-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="d660f-111">Örneğin, tür `class Dict<String,int32>`ise `EnumerateTypeParameters`, `String` ve `int32` sırayla temsil eden nesneleri içeren bir `ICorDebugTypeEnum` döndürür.</span><span class="sxs-lookup"><span data-stu-id="d660f-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
- <span data-ttu-id="d660f-112">ELEMENT_TYPE_FNPTR: `ICorDebugTypeEnum` içindeki tür parametrelerinin sayısı, işlev tarafından kabul edilen bağımsız değişkenlerin sayısından bir büyük olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d660f-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="d660f-113">`ICorDebugTypeEnum` yer alan ilk tür parametresi, işlevin dönüş türüdür ve sonraki tür parametreleri işlevin parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="d660f-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
- <span data-ttu-id="d660f-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF veya ELEMENT_TYPE_PTR: bir tür parametresi döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="d660f-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="d660f-115">Örneğin, türü `int32[]`gibi bir dizi türü ise`EnumerateTypeParameters`, `int32`temsil eden bir nesne içeren bir `ICorDebugTypeEnum` döndürür.</span><span class="sxs-lookup"><span data-stu-id="d660f-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d660f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d660f-116">Requirements</span></span>  
 <span data-ttu-id="d660f-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d660f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d660f-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d660f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d660f-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d660f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d660f-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d660f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
