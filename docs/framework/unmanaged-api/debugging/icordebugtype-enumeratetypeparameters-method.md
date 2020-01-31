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
ms.openlocfilehash: b2c381d093069f5ee86be1b19d75f5c2d69ad9fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791307"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="ca95b-102">ICorDebugType::EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca95b-102">ICorDebugType::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="ca95b-103">Bu ICorDebugType tarafından başvurulan sınıfın <xref:System.Type> parametrelerini içeren bir ICorDebugTypeEnum için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ca95b-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca95b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca95b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca95b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca95b-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="ca95b-106">dışı Türün parametrelerini içeren `ICorDebugTypeEnum` adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ca95b-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca95b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca95b-107">Remarks</span></span>  
 <span data-ttu-id="ca95b-108">[ICorDebugType:: GetType](icordebugtype-gettype-method.md) tarafından döndürülen CorElementType değeri ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR veya ELEMENT_TYPE_FNPTR ise `EnumerateTypeParameters` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca95b-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="ca95b-109">Parametrelerin sayısı ve sırası türüne bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="ca95b-109">The number of parameters and their order depends on the type:</span></span>  
  
- <span data-ttu-id="ca95b-110">ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE: Bu yöntemin döndürdüğü `ICorDebugTypeEnum` içerilen tür parametrelerinin sayısı, karşılık gelen sınıf için biçimsel tür parametrelerinin sayısına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ca95b-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="ca95b-111">Örneğin, tür `class Dict<String,int32>`ise `EnumerateTypeParameters`, `String` ve `int32` sırayla temsil eden nesneleri içeren bir `ICorDebugTypeEnum` döndürür.</span><span class="sxs-lookup"><span data-stu-id="ca95b-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
- <span data-ttu-id="ca95b-112">ELEMENT_TYPE_FNPTR: `ICorDebugTypeEnum` içindeki tür parametrelerinin sayısı, işlev tarafından kabul edilen bağımsız değişken sayısından bir daha büyük olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ca95b-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="ca95b-113">`ICorDebugTypeEnum` yer alan ilk tür parametresi, işlevin dönüş türüdür ve sonraki tür parametreleri işlevin parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="ca95b-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
- <span data-ttu-id="ca95b-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF veya ELEMENT_TYPE_PTR: bir tür parametresi döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="ca95b-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="ca95b-115">Örneğin, türü `int32[]`gibi bir dizi türü ise`EnumerateTypeParameters`, `int32`temsil eden bir nesne içeren bir `ICorDebugTypeEnum` döndürür.</span><span class="sxs-lookup"><span data-stu-id="ca95b-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca95b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca95b-116">Requirements</span></span>  
 <span data-ttu-id="ca95b-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca95b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca95b-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ca95b-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca95b-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ca95b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca95b-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca95b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
