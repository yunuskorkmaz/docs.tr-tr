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
ms.openlocfilehash: 8210e67f4bdd615ff65d9bd3474043fc45fd8883
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791253"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="face7-102">ICorDebugType Arabirimi</span><span class="sxs-lookup"><span data-stu-id="face7-102">ICorDebugType Interface</span></span>
<span data-ttu-id="face7-103">Temel veya karmaşık (yani Kullanıcı tanımlı) bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="face7-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="face7-104">Tür geneldir ise, `ICorDebugType` örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="face7-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="face7-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="face7-105">Methods</span></span>  
  
|<span data-ttu-id="face7-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="face7-106">Method</span></span>|<span data-ttu-id="face7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="face7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="face7-108">EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="face7-108">EnumerateTypeParameters Method</span></span>](icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="face7-109">Bu `ICorDebugType`tarafından başvurulan sınıfın genel <xref:System.Type> parametrelerine başvuran bir ICorDebugTypeEnum için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="face7-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="face7-110">GetBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="face7-110">GetBase Method</span></span>](icordebugtype-getbase-method.md)|<span data-ttu-id="face7-111">Bu `ICorDebugType`tarafından başvurulan sınıfın temel sınıfına başvuran bir `ICorDebugType` için bir arabirim işaretçisi alır, varsa.</span><span class="sxs-lookup"><span data-stu-id="face7-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="face7-112">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="face7-112">GetClass Method</span></span>](icordebugtype-getclass-method.md)|<span data-ttu-id="face7-113">Bu `ICorDebugType`türü belirtilmiş oluşturucuya başvuran bir ICorDebugClass için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="face7-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="face7-114">GetFirstTypeParameter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="face7-114">GetFirstTypeParameter Method</span></span>](icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="face7-115">Bu `ICorDebugType`tarafından başvurulan sınıfın oluşturucusunun ilk genel <xref:System.Type> parametresine başvuran bir `ICorDebugType` için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="face7-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="face7-116">GetRank Yöntemi</span><span class="sxs-lookup"><span data-stu-id="face7-116">GetRank Method</span></span>](icordebugtype-getrank-method.md)|<span data-ttu-id="face7-117">Bir dizi türündeki boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="face7-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="face7-118">GetStaticFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="face7-118">GetStaticFieldValue Method</span></span>](icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="face7-119">Belirtilen yığın çerçevesindeki belirtilen alan belirtecinin başvurduğu statik alanın değerini içeren bir ICorDebugValue için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="face7-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="face7-120">GetType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="face7-120">GetType Method</span></span>](icordebugtype-gettype-method.md)|<span data-ttu-id="face7-121">Bu `ICorDebugType`başvurduğu ortak dil çalışma zamanının yerel türünü tanımlayan bir CorElementType değeri alır <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="face7-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="face7-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="face7-122">Remarks</span></span>  
 <span data-ttu-id="face7-123">Tür geneldir ise `ICorDebugClass` örneklenmiş türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="face7-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="face7-124">`ICorDebugType` arabirimi bir örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="face7-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="face7-125">Örneğin, Hashtable\<K, V > `ICorDebugClass`tarafından temsil edilebilir, ancak Hashtable\<Int32, String > ise `ICorDebugType`olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="face7-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="face7-126">Genel olmayan türler hem `ICorDebugClass` hem de `ICorDebugType`ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="face7-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="face7-127">İkinci arabirim, tür örneği oluşturma ile başa çıkmak için .NET Framework sürüm 2,0 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="face7-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="face7-128">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="face7-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="face7-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="face7-129">Requirements</span></span>  
 <span data-ttu-id="face7-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="face7-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="face7-131">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="face7-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="face7-132">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="face7-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="face7-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="face7-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="face7-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="face7-134">See also</span></span>

- [<span data-ttu-id="face7-135">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="face7-135">Debugging Interfaces</span></span>](debugging-interfaces.md)
