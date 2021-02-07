---
description: ': ICorDebugClass2:: GetParameterizedType yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4810e10e88af9256a466579ee607c0ef314d984b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765045"
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="8127b-103">ICorDebugClass2::GetParameterizedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8127b-103">ICorDebugClass2::GetParameterizedType Method</span></span>

<span data-ttu-id="8127b-104">Bu sınıf için tür bildirimini alır.</span><span class="sxs-lookup"><span data-stu-id="8127b-104">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8127b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8127b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8127b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8127b-106">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="8127b-107">'ndaki Bu sınıf için öğe türünü belirten CorElementType numaralandırması değeri: Bu ICorDebugClass2 bir değer türünü temsil ediyorsa, bu değeri ELEMENT_TYPE_VALUETYPE olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8127b-107">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="8127b-108">Bu bir karmaşık türü temsil ediyorsa, bu değeri ELEMENT_TYPE_CLASS olarak ayarlayın `ICorDebugClass2` .</span><span class="sxs-lookup"><span data-stu-id="8127b-108">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="8127b-109">'ndaki Tür genel ise tür parametrelerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="8127b-109">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="8127b-110">Tür parametrelerinin sayısı (varsa), sınıfının gerektirdiği sayıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="8127b-110">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="8127b-111">'ndaki Her biri bir tür parametresini temsil eden ICorDebugType nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="8127b-111">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="8127b-112">Sınıf genel değilse, bu değer null olur.</span><span class="sxs-lookup"><span data-stu-id="8127b-112">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="8127b-113">dışı `ICorDebugType` Tür bildirimini temsil eden nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8127b-113">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="8127b-114">Bu nesne, <xref:System.Type> Yönetilen koddaki bir nesneye eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="8127b-114">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8127b-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8127b-115">Remarks</span></span>  

 <span data-ttu-id="8127b-116">Sınıf genel değilse, diğer bir deyişle, tür parametreleri yoksa, `GetParameterizedType` sınıfa karşılık gelen çalışma zamanı türü nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="8127b-116">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="8127b-117">Parametre, sınıf `elementType` için doğru öğe türüne ayarlanmalıdır: element_type_valuetype sınıf bir değer türüdür; Aksi takdirde, element_type_class.</span><span class="sxs-lookup"><span data-stu-id="8127b-117">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="8127b-118">Sınıf tür parametrelerini kabul ederse (örneğin, `ArrayList<T>` ), `GetParameterizedType` gibi bir örneklenmiş tür için bir tür nesnesi oluşturmak için kullanabilirsiniz `ArrayList<int>` .</span><span class="sxs-lookup"><span data-stu-id="8127b-118">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="8127b-119">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="8127b-119">Background Information</span></span>  

 <span data-ttu-id="8127b-120">1,0 ve 1,1 .NET Framework sürümlerinde, Meta verilerdeki her tür çalışan işlemdeki bir türle doğrudan eşleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8127b-120">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="8127b-121">Bu nedenle, meta veri türü ve çalışma zamanı türü, çalışan işlemde tek bir gösterimine sahipti.</span><span class="sxs-lookup"><span data-stu-id="8127b-121">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="8127b-122">Ancak, Meta verilerdeki bir genel tür, çalışan işlemdeki türdeki birçok farklı örneklememe eşleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8127b-122">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="8127b-123">Örneğin, meta veri türü,,, vb `SortedList<K,V>` . ile eşlenir `SortedList<String, EmployeeRecord>` `SortedList<Int32, String>` `SortedList<String,Array<Int32>>` .</span><span class="sxs-lookup"><span data-stu-id="8127b-123">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="8127b-124">Bu nedenle, tür örnek oluşturmayı işlemek için bir yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="8127b-124">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="8127b-125">.NET Framework sürüm 2,0 `ICorDebugType` arabirimini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="8127b-125">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="8127b-126">Genel bir tür için, `ICorDebugClass` veya `ICorDebugClass2` nesnesi örneklenmiş türü () temsil eder `SortedList<K,V>` ve bir nesne, `ICorDebugType` çeşitli örneklenmiş türleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8127b-126">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="8127b-127">Bir `ICorDebugClass` veya `ICorDebugClass2` nesnesi verildiğinde, `ICorDebugType` yöntemini çağırarak herhangi bir örnek oluşturma için bir nesne oluşturabilirsiniz `ICorDebugClass2::GetParameterizedType` .</span><span class="sxs-lookup"><span data-stu-id="8127b-127">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="8127b-128">Ayrıca `ICorDebugType` , Int32 gibi basit bir tür için veya genel olmayan bir tür için bir nesne oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8127b-128">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="8127b-129">`ICorDebugType`Bir türün çalışma zamanı kavramının temsil edilebilmesi için nesnenin giriş, API 'nin tamamında Ripple etkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8127b-129">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="8127b-130">Daha önce bir `ICorDebugClass` veya `ICorDebugClass2` nesnesi veya hatta bir değeri geçen işlevler `CorElementType` , bir nesneyi almak için genelleştirilir `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="8127b-130">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8127b-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8127b-131">Requirements</span></span>  

 <span data-ttu-id="8127b-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8127b-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8127b-133">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8127b-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8127b-134">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8127b-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8127b-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8127b-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
