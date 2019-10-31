---
title: ICorDebugClass2::GetParameterizedType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.GetParameterizedType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type:
- apiref
ms.openlocfilehash: 64537ab97c1256cc6f963999b027bafc25cbbccb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125738"
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="a49fe-102">ICorDebugClass2::GetParameterizedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a49fe-102">ICorDebugClass2::GetParameterizedType Method</span></span>
<span data-ttu-id="a49fe-103">Bu sınıf için tür bildirimini alır.</span><span class="sxs-lookup"><span data-stu-id="a49fe-103">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a49fe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a49fe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a49fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a49fe-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="a49fe-106">'ndaki Bu sınıf için öğe türünü belirten CorElementType numaralandırması değeri: Bu ICorDebugClass2 bir değer türünü temsil ediyorsa, bu değeri ELEMENT_TYPE_VALUETYPE olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a49fe-106">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="a49fe-107">Bu `ICorDebugClass2` karmaşık bir türü temsil ediyorsa, bu değeri ELEMENT_TYPE_CLASS olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a49fe-107">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="a49fe-108">'ndaki Tür genel ise tür parametrelerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="a49fe-108">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="a49fe-109">Tür parametrelerinin sayısı (varsa), sınıfının gerektirdiği sayıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="a49fe-109">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="a49fe-110">'ndaki Her biri bir tür parametresini temsil eden ICorDebugType nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="a49fe-110">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="a49fe-111">Sınıf genel değilse, bu değer null olur.</span><span class="sxs-lookup"><span data-stu-id="a49fe-111">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="a49fe-112">dışı Tür bildirimini temsil eden bir `ICorDebugType` nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a49fe-112">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="a49fe-113">Bu nesne, Yönetilen koddaki <xref:System.Type> nesnesine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="a49fe-113">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a49fe-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a49fe-114">Remarks</span></span>  
 <span data-ttu-id="a49fe-115">Sınıf genel değilse, yani tür parametreleri yoksa, `GetParameterizedType` yalnızca sınıfa karşılık gelen çalışma zamanı türü nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="a49fe-115">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="a49fe-116">Sınıf bir değer türünde ise `elementType` parametresi, sınıf için doğru öğe türüne ayarlanmalıdır: ELEMENT_TYPE_VALUETYPE; Aksi takdirde, ELEMENT_TYPE_CLASS.</span><span class="sxs-lookup"><span data-stu-id="a49fe-116">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="a49fe-117">Sınıf tür parametrelerini kabul ediyorsa (örneğin, `ArrayList<T>`), `ArrayList<int>`gibi bir örneklenmiş tür için bir tür nesnesi oluşturmak üzere `GetParameterizedType` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a49fe-117">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="a49fe-118">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="a49fe-118">Background Information</span></span>  
 <span data-ttu-id="a49fe-119">1,0 ve 1,1 .NET Framework sürümlerinde, Meta verilerdeki her tür çalışan işlemdeki bir türle doğrudan eşleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a49fe-119">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="a49fe-120">Bu nedenle, meta veri türü ve çalışma zamanı türü, çalışan işlemde tek bir gösterimine sahipti.</span><span class="sxs-lookup"><span data-stu-id="a49fe-120">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="a49fe-121">Ancak, Meta verilerdeki bir genel tür, çalışan işlemdeki türdeki birçok farklı örneklememe eşleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a49fe-121">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="a49fe-122">Örneğin, `SortedList<K,V>` meta veri türü `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`vb. ile eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a49fe-122">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="a49fe-123">Bu nedenle, tür örnek oluşturmayı işlemek için bir yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="a49fe-123">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="a49fe-124">.NET Framework sürüm 2,0 `ICorDebugType` arabirimini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="a49fe-124">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="a49fe-125">Genel bir tür için, bir `ICorDebugClass` veya `ICorDebugClass2` nesnesi örneklenmiş türü (`SortedList<K,V>`) temsil eder ve bir `ICorDebugType` nesnesi çeşitli örneklenmiş türleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a49fe-125">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="a49fe-126">`ICorDebugClass` veya `ICorDebugClass2` nesnesi verildiğinde, `ICorDebugClass2::GetParameterizedType` yöntemini çağırarak herhangi bir örnekleme için `ICorDebugType` nesnesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a49fe-126">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="a49fe-127">Ayrıca, Int32 gibi basit bir tür için veya genel olmayan bir tür için `ICorDebugType` bir nesne oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a49fe-127">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="a49fe-128">Bir türün çalışma zamanı kavramının temsil edilebilmesi için `ICorDebugType` nesnesine giriş, API 'nin tamamında Ripple etkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a49fe-128">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="a49fe-129">Daha önce bir `ICorDebugClass` veya `ICorDebugClass2` nesnesi geçen veya hatta `CorElementType` değeri `ICorDebugType` bir nesne almak için genelleştirilmiş işlevlerdir.</span><span class="sxs-lookup"><span data-stu-id="a49fe-129">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a49fe-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a49fe-130">Requirements</span></span>  
 <span data-ttu-id="a49fe-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a49fe-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a49fe-132">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a49fe-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a49fe-133">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a49fe-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a49fe-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a49fe-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
