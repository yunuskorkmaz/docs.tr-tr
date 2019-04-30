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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e1734ca91fd48cc15b8dbf25f11518ed0455b6f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750780"
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="98e24-102">ICorDebugClass2::GetParameterizedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98e24-102">ICorDebugClass2::GetParameterizedType Method</span></span>
<span data-ttu-id="98e24-103">Bu sınıf türü bildirimi alır.</span><span class="sxs-lookup"><span data-stu-id="98e24-103">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98e24-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98e24-104">Syntax</span></span>  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98e24-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98e24-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="98e24-106">[in] Bu sınıf için öğe türü belirtir CorElementType sabit listesi değeri: Bu Icordebugclass2 bir değer türü temsil ediyorsa ELEMENT_TYPE_VALUETYPE için bu değeri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="98e24-106">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="98e24-107">Bu değer için ELEMENT_TYPE_CLASS bu verilirse `ICorDebugClass2` karmaşık bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="98e24-107">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="98e24-108">[in] Tür genelse, tür parametreleri, sayısı.</span><span class="sxs-lookup"><span data-stu-id="98e24-108">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="98e24-109">Tür parametreleri (varsa) sayısı, sınıf tarafından gerekli numarası aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98e24-109">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="98e24-110">[in] Bir dizi işaretçileri, her biri bir tür parametresini temsil eden bir Icordebugtype nesneye işaret eder.</span><span class="sxs-lookup"><span data-stu-id="98e24-110">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="98e24-111">Genel olmayan sınıf ise bu değer null olur.</span><span class="sxs-lookup"><span data-stu-id="98e24-111">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="98e24-112">[out] Adresine bir işaretçi bir `ICorDebugType` türü bildirimini temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="98e24-112">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="98e24-113">Bu nesne değerine eşdeğer olan bir <xref:System.Type> yönetilen kodda nesne.</span><span class="sxs-lookup"><span data-stu-id="98e24-113">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98e24-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98e24-114">Remarks</span></span>  
 <span data-ttu-id="98e24-115">Hiçbir tür parametreleri varsa, sınıf başka bir deyişle, genel olmayan, ise `GetParameterizedType` yalnızca sınıfına karşılık gelen çalışma zamanı tür nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="98e24-115">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="98e24-116">`elementType` Parametre sınıfı için doğru öğe türü ayarlanmalıdır: Sınıf bir değer türü ise ELEMENT_TYPE_VALUETYPE; Aksi takdirde, ELEMENT_TYPE_CLASS.</span><span class="sxs-lookup"><span data-stu-id="98e24-116">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="98e24-117">Sınıf türü parametreleri kabul ediyorsa (örneğin, `ArrayList<T>`), kullanabileceğiniz `GetParameterizedType` gibi örneklenmiş bir tür için bir tür nesnesi oluşturmak için `ArrayList<int>`.</span><span class="sxs-lookup"><span data-stu-id="98e24-117">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="98e24-118">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="98e24-118">Background Information</span></span>  
 <span data-ttu-id="98e24-119">.NET Framework sürüm 1.0 ve 1.1, her tür meta verilerinde doğrudan bir çalışan işlem türüne eşleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="98e24-119">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="98e24-120">Bu nedenle, bir meta veri türü ve çalışma zamanı türü tek bir gösterimiyse çalışan işleminde vardı.</span><span class="sxs-lookup"><span data-stu-id="98e24-120">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="98e24-121">Ancak, bir genel tür meta verilerinde birçok farklı örneklemeleri çalışan işlemindeki türü eşlenebilir.</span><span class="sxs-lookup"><span data-stu-id="98e24-121">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="98e24-122">Örneğin, meta veri türü `SortedList<K,V>` eşleyebilirsiniz `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="98e24-122">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="98e24-123">Bu nedenle, tür örneği oluşturmada işlemek için bir yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="98e24-123">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="98e24-124">.NET Framework sürüm 2.0 tanıtır `ICorDebugType` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="98e24-124">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="98e24-125">Genel bir tür için bir `ICorDebugClass` veya `ICorDebugClass2` nesne örneklenmemiş türü temsil eder (`SortedList<K,V>`) ve bir `ICorDebugType` nesne örneklenmiş çeşitli temsil eder.</span><span class="sxs-lookup"><span data-stu-id="98e24-125">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="98e24-126">Verilen bir `ICorDebugClass` veya `ICorDebugClass2` nesnesi oluşturmak için kullanabileceğiniz bir `ICorDebugType` çağırarak tüm örneklemesi için nesne `ICorDebugClass2::GetParameterizedType` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="98e24-126">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="98e24-127">Ayrıca oluşturabileceğiniz bir `ICorDebugType` Int32 gibi basit bir tür için veya genel olmayan bir tür için bir nesne.</span><span class="sxs-lookup"><span data-stu-id="98e24-127">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="98e24-128">Giriş `ICorDebugType` bir tür çalışma zamanı kavramını temsil etmek için nesnesi API boyunca bir dalgalanma etkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="98e24-128">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="98e24-129">Daha önce geçen işlevler bir `ICorDebugClass` veya `ICorDebugClass2` nesne veya hatta bir `CorElementType` değeri genelleştirilmiş gerçekleştirilecek bir `ICorDebugType` nesne.</span><span class="sxs-lookup"><span data-stu-id="98e24-129">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98e24-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98e24-130">Requirements</span></span>  
 <span data-ttu-id="98e24-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98e24-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98e24-132">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98e24-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98e24-133">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98e24-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98e24-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98e24-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
