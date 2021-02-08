---
description: ': ICorDebugType arabirimi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 4cd668263906ef21e1bb665795425ca3a239c2bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800896"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="7e74e-103">ICorDebugType Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e74e-103">ICorDebugType Interface</span></span>

<span data-ttu-id="7e74e-104">Temel veya karmaşık (yani Kullanıcı tanımlı) bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7e74e-104">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="7e74e-105">Tür geneldir ise, `ICorDebugType` örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7e74e-105">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e74e-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7e74e-106">Methods</span></span>  
  
|<span data-ttu-id="7e74e-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7e74e-107">Method</span></span>|<span data-ttu-id="7e74e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e74e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e74e-109">EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e74e-109">EnumerateTypeParameters Method</span></span>](icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="7e74e-110">Bu tarafından başvurulan sınıfın genel parametrelerine başvuran ICorDebugTypeEnum için bir arabirim işaretçisi alır <xref:System.Type> `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="7e74e-110">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="7e74e-111">GetBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e74e-111">GetBase Method</span></span>](icordebugtype-getbase-method.md)|<span data-ttu-id="7e74e-112">Bir `ICorDebugType` tane varsa, bunun başvurduğu sınıfın temel sınıfına başvuran bir arabirim işaretçisi alır `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="7e74e-112">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="7e74e-113">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e74e-113">GetClass Method</span></span>](icordebugtype-getclass-method.md)|<span data-ttu-id="7e74e-114">Bu bir ICorDebugClass 'ın türü belirtilmiş oluşturucusuna başvuran bir arabirim işaretçisi alır `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="7e74e-114">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="7e74e-115">GetFirstTypeParameter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e74e-115">GetFirstTypeParameter Method</span></span>](icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="7e74e-116">`ICorDebugType` <xref:System.Type> Tarafından başvurulan sınıfın oluşturucusunun ilk genel parametresine başvuran bir arabirim işaretçisi alır `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="7e74e-116">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="7e74e-117">GetRank Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e74e-117">GetRank Method</span></span>](icordebugtype-getrank-method.md)|<span data-ttu-id="7e74e-118">Bir dizi türündeki boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="7e74e-118">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="7e74e-119">GetStaticFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e74e-119">GetStaticFieldValue Method</span></span>](icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="7e74e-120">Belirtilen yığın çerçevesindeki belirtilen alan belirtecinin başvurduğu statik alanın değerini içeren bir ICorDebugValue için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="7e74e-120">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="7e74e-121">GetType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e74e-121">GetType Method</span></span>](icordebugtype-gettype-method.md)|<span data-ttu-id="7e74e-122">Bunun başvurduğu ortak dil çalışma zamanının yerel türünü açıklayan bir CorElementType değeri alır <xref:System.Type> `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="7e74e-122">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e74e-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e74e-123">Remarks</span></span>  

 <span data-ttu-id="7e74e-124">Tür geneldir ise, `ICorDebugClass` örneklenmemiş türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7e74e-124">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="7e74e-125">`ICorDebugType`Arabirim, bir örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7e74e-125">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="7e74e-126">Örneğin, Hashtable \<K, V> tarafından temsil edilir `ICorDebugClass` , ancak Hashtable \<Int32, String> tarafından temsil edilir `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="7e74e-126">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="7e74e-127">Genel olmayan türler hem hem de ile temsil `ICorDebugClass` edilir `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="7e74e-127">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="7e74e-128">İkinci arabirim, tür örneği oluşturma ile başa çıkmak için .NET Framework sürüm 2,0 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="7e74e-128">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e74e-129">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="7e74e-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e74e-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e74e-130">Requirements</span></span>  

 <span data-ttu-id="7e74e-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e74e-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e74e-132">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7e74e-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e74e-133">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7e74e-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e74e-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e74e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e74e-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e74e-135">See also</span></span>

- [<span data-ttu-id="7e74e-136">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7e74e-136">Debugging Interfaces</span></span>](debugging-interfaces.md)
