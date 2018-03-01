---
title: Icordebugtype Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 503d0debef2ec1bebd674234051db8101dcb0de2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtype-interface1"></a><span data-ttu-id="914ea-102">Icordebugtype Interface1</span><span class="sxs-lookup"><span data-stu-id="914ea-102">ICorDebugType Interface1</span></span>
<span data-ttu-id="914ea-103">(Kullanıcı tanımlı olan) bir türü, temel veya karmaşık temsil eder.</span><span class="sxs-lookup"><span data-stu-id="914ea-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="914ea-104">Tür genel, ise `ICorDebugType` oluşturulmuş genel türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="914ea-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="914ea-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="914ea-105">Methods</span></span>  
  
|<span data-ttu-id="914ea-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="914ea-106">Method</span></span>|<span data-ttu-id="914ea-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="914ea-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="914ea-108">EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="914ea-108">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="914ea-109">Arabirim işaretçisi genel başvuruda bulunan bir Icordebugtypeenum alır <xref:System.Type> bu tarafından başvurulan sınıfı parametrelerinin `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="914ea-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="914ea-110">GetBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="914ea-110">GetBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|<span data-ttu-id="914ea-111">Bir arabirim işaretçisi alır bir `ICorDebugType` bu tarafından başvurulan sınıfın temel sınıf başvuran `ICorDebugType`, varsa.</span><span class="sxs-lookup"><span data-stu-id="914ea-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="914ea-112">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="914ea-112">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|<span data-ttu-id="914ea-113">Bu yazılan Oluşturucusu başvuruda bulunan bir Icordebugclass arabirimi işaretçisi alır `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="914ea-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="914ea-114">GetFirstTypeParameter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="914ea-114">GetFirstTypeParameter Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="914ea-115">Bir arabirim işaretçisi alır bir `ICorDebugType` ilk genel başvuran <xref:System.Type> parametresi bu tarafından başvurulan sınıf için `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="914ea-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="914ea-116">GetRank Yöntemi</span><span class="sxs-lookup"><span data-stu-id="914ea-116">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|<span data-ttu-id="914ea-117">Dimensions sayısı bir dizi türünü alır.</span><span class="sxs-lookup"><span data-stu-id="914ea-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="914ea-118">GetStaticFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="914ea-118">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="914ea-119">Arabirim işaretçisi belirtilen alanı tarafından başvurulan statik alanın değerini içeren bir Icordebugvalue için belirtilen yığın çerçevesinde belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="914ea-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="914ea-120">GetType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="914ea-120">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|<span data-ttu-id="914ea-121">Ortak dil çalışma zamanı yerel türünü tanımlayan bir CorElementType değeri alır <xref:System.Type> bu tarafından başvurulan `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="914ea-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="914ea-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="914ea-122">Remarks</span></span>  
 <span data-ttu-id="914ea-123">Tür genel, ise `ICorDebugClass` dizilerine türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="914ea-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="914ea-124">`ICorDebugType` Arabirimi bir oluşturulmuş genel tür temsil eder.</span><span class="sxs-lookup"><span data-stu-id="914ea-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="914ea-125">Örneğin, Hashtable\<K, V > gösterdiği `ICorDebugClass`, ancak Hashtable\<Int32, dize > gösterdiği `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="914ea-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="914ea-126">Olmayan genel türleri temsil edilen her ikisi için de `ICorDebugClass` ve `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="914ea-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="914ea-127">İkinci arabirim türü örnek oluşturma ile mücadele etmek için .NET Framework sürüm 2.0 sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="914ea-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="914ea-128">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="914ea-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="914ea-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="914ea-129">Requirements</span></span>  
 <span data-ttu-id="914ea-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="914ea-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="914ea-131">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="914ea-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="914ea-132">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="914ea-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="914ea-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="914ea-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="914ea-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="914ea-134">See Also</span></span>  
 [<span data-ttu-id="914ea-135">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="914ea-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
