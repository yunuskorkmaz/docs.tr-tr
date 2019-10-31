---
title: ICorDebugClass Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
ms.openlocfilehash: 5714597b5e5ca2936aad53217ae934684e75585c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125743"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="f16f9-102">ICorDebugClass Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f16f9-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="f16f9-103">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f16f9-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="f16f9-104">Tür geneldir ise, `ICorDebugClass` örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f16f9-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f16f9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f16f9-105">Methods</span></span>  
  
|<span data-ttu-id="f16f9-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f16f9-106">Method</span></span>|<span data-ttu-id="f16f9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f16f9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f16f9-108">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f16f9-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="f16f9-109">Bu sınıfı tanımlayan modülü alır.</span><span class="sxs-lookup"><span data-stu-id="f16f9-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="f16f9-110">GetStaticFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f16f9-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="f16f9-111">Belirtilen statik alanın değerini alır.</span><span class="sxs-lookup"><span data-stu-id="f16f9-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="f16f9-112">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f16f9-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="f16f9-113">Bu sınıf için `TypeDef` meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="f16f9-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f16f9-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f16f9-114">Remarks</span></span>  
 <span data-ttu-id="f16f9-115">`ICorDebugClass` arabirimi örneği oluşturulmuş bir genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f16f9-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="f16f9-116">ICorDebugType arabirimi bir örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f16f9-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="f16f9-117">Örneğin, `Hashtable<K, V>` `ICorDebugClass`tarafından temsil edilir, ancak `Hashtable<Int32, String>` `ICorDebugType`tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="f16f9-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="f16f9-118">Genel olmayan türler hem `ICorDebugClass` hem de `ICorDebugType`ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="f16f9-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="f16f9-119">İkinci arabirim, tür örneği oluşturma ile başa çıkmak için .NET Framework sürüm 2,0 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="f16f9-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f16f9-120">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="f16f9-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f16f9-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f16f9-121">Requirements</span></span>  
 <span data-ttu-id="f16f9-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f16f9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f16f9-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f16f9-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f16f9-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f16f9-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f16f9-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f16f9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f16f9-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f16f9-126">See also</span></span>

- [<span data-ttu-id="f16f9-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f16f9-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
