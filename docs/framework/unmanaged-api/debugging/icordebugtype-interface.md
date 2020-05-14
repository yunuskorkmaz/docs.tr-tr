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
ms.openlocfilehash: 5e88652ff75223e30e6abc454f1e1af91494c7b2
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396697"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="ad51e-102">ICorDebugType Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad51e-102">ICorDebugType Interface</span></span>
<span data-ttu-id="ad51e-103">Temel veya karmaşık (yani Kullanıcı tanımlı) bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ad51e-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="ad51e-104">Tür geneldir ise, `ICorDebugType` örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ad51e-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad51e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ad51e-105">Methods</span></span>  
  
|<span data-ttu-id="ad51e-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ad51e-106">Method</span></span>|<span data-ttu-id="ad51e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad51e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ad51e-108">EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad51e-108">EnumerateTypeParameters Method</span></span>](icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="ad51e-109">Bu tarafından başvurulan sınıfın genel parametrelerine başvuran ICorDebugTypeEnum için bir arabirim işaretçisi alır <xref:System.Type> `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="ad51e-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="ad51e-110">GetBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad51e-110">GetBase Method</span></span>](icordebugtype-getbase-method.md)|<span data-ttu-id="ad51e-111">Bir `ICorDebugType` tane varsa, bunun başvurduğu sınıfın temel sınıfına başvuran bir arabirim işaretçisi alır `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="ad51e-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="ad51e-112">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad51e-112">GetClass Method</span></span>](icordebugtype-getclass-method.md)|<span data-ttu-id="ad51e-113">Bu bir ICorDebugClass 'ın türü belirtilmiş oluşturucusuna başvuran bir arabirim işaretçisi alır `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="ad51e-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="ad51e-114">GetFirstTypeParameter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad51e-114">GetFirstTypeParameter Method</span></span>](icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="ad51e-115">`ICorDebugType` <xref:System.Type> Tarafından başvurulan sınıfın oluşturucusunun ilk genel parametresine başvuran bir arabirim işaretçisi alır `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="ad51e-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="ad51e-116">GetRank Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad51e-116">GetRank Method</span></span>](icordebugtype-getrank-method.md)|<span data-ttu-id="ad51e-117">Bir dizi türündeki boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="ad51e-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="ad51e-118">GetStaticFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad51e-118">GetStaticFieldValue Method</span></span>](icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="ad51e-119">Belirtilen yığın çerçevesindeki belirtilen alan belirtecinin başvurduğu statik alanın değerini içeren bir ICorDebugValue için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ad51e-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="ad51e-120">GetType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad51e-120">GetType Method</span></span>](icordebugtype-gettype-method.md)|<span data-ttu-id="ad51e-121">Bunun başvurduğu ortak dil çalışma zamanının yerel türünü açıklayan bir CorElementType değeri alır <xref:System.Type> `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="ad51e-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad51e-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad51e-122">Remarks</span></span>  
 <span data-ttu-id="ad51e-123">Tür geneldir ise, `ICorDebugClass` örneklenmemiş türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ad51e-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="ad51e-124">`ICorDebugType`Arabirim, bir örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ad51e-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="ad51e-125">Örneğin, Hashtable \< K, V> tarafından temsil edilir `ICorDebugClass` , ancak Hashtable \< ınt32, String> tarafından temsil edilir `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="ad51e-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="ad51e-126">Genel olmayan türler hem hem de ile temsil `ICorDebugClass` edilir `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="ad51e-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="ad51e-127">İkinci arabirim, tür örneği oluşturma ile başa çıkmak için .NET Framework sürüm 2,0 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="ad51e-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad51e-128">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="ad51e-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad51e-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad51e-129">Requirements</span></span>  
 <span data-ttu-id="ad51e-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad51e-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad51e-131">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ad51e-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad51e-132">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ad51e-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad51e-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad51e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad51e-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad51e-134">See also</span></span>

- [<span data-ttu-id="ad51e-135">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ad51e-135">Debugging Interfaces</span></span>](debugging-interfaces.md)
