---
title: ICorDebugType Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74863af1096f8600b8095e593c1f3c820c512e9d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166809"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="ae84e-102">ICorDebugType Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae84e-102">ICorDebugType Interface</span></span>
<span data-ttu-id="ae84e-103">(Kullanıcı tanımlı olan) bir türü, basit veya karmaşık temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ae84e-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="ae84e-104">Tür genelse, `ICorDebugType` örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ae84e-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae84e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ae84e-105">Methods</span></span>  
  
|<span data-ttu-id="ae84e-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ae84e-106">Method</span></span>|<span data-ttu-id="ae84e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae84e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae84e-108">EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae84e-108">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="ae84e-109">Genel başvuran bir Icordebugtypeenum bir arabirim işaretçisi alır <xref:System.Type> bu tarafından başvurulan sınıfın parametrelerinin `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="ae84e-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="ae84e-110">GetBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae84e-110">GetBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|<span data-ttu-id="ae84e-111">Bir arabirim işaretçisi alır bir `ICorDebugType` bu tarafından başvurulan sınıfın temel sınıfına başvuran `ICorDebugType`, varsa.</span><span class="sxs-lookup"><span data-stu-id="ae84e-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="ae84e-112">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae84e-112">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|<span data-ttu-id="ae84e-113">Bu yazılı oluşturucusuna başvuran bir Icordebugclass bir arabirim işaretçisi alır `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="ae84e-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="ae84e-114">GetFirstTypeParameter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae84e-114">GetFirstTypeParameter Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="ae84e-115">Bir arabirim işaretçisi alır bir `ICorDebugType` ilk genel başvuran <xref:System.Type> bu tarafından başvurulan sınıfın oluşturucusu için parametresi `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="ae84e-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="ae84e-116">GetRank Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae84e-116">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|<span data-ttu-id="ae84e-117">Bir dizi türü boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="ae84e-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="ae84e-118">GetStaticFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae84e-118">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="ae84e-119">Bir arabirim işaretçisi için belirtilen alan tarafından başvurulan statik alanı değerini içeren bir Icordebugvalue belirtilen yığın çerçevesinde belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="ae84e-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="ae84e-120">GetType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae84e-120">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|<span data-ttu-id="ae84e-121">Ortak dil çalışma zamanı yerel türünü açıklayan bir CorElementType değerini alır <xref:System.Type> bu tarafından başvurulan `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="ae84e-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae84e-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae84e-122">Remarks</span></span>  
 <span data-ttu-id="ae84e-123">Tür genelse, `ICorDebugClass` örneklenmemiş türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ae84e-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="ae84e-124">`ICorDebugType` Arabirimi örneklenmiş bir genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ae84e-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="ae84e-125">Örneğin, karma tablosu\<K, V > tarafından temsil edilir `ICorDebugClass`bilgileriyse Hashtable\<Int32, String > tarafından temsil edilir `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="ae84e-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="ae84e-126">Genel olmayan türler tarafından temsil edilir `ICorDebugClass` ve `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="ae84e-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="ae84e-127">İkinci arabirim tür örneği oluşturmada ile uğraşmak için .NET Framework sürüm 2.0 kullanılmaya başlandı.</span><span class="sxs-lookup"><span data-stu-id="ae84e-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae84e-128">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ae84e-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae84e-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae84e-129">Requirements</span></span>  
 <span data-ttu-id="ae84e-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae84e-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae84e-131">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae84e-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae84e-132">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae84e-132">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ae84e-133">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ae84e-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ae84e-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae84e-134">See also</span></span>

- [<span data-ttu-id="ae84e-135">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ae84e-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
