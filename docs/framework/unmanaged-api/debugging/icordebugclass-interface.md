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
ms.openlocfilehash: 7ac588591222a1abbc7b99ec7e973284c055f95e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784162"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="b2888-102">ICorDebugClass Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2888-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="b2888-103">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b2888-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="b2888-104">Tür geneldir ise, `ICorDebugClass` örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b2888-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2888-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b2888-105">Methods</span></span>  
  
|<span data-ttu-id="b2888-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b2888-106">Method</span></span>|<span data-ttu-id="b2888-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2888-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2888-108">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2888-108">GetModule Method</span></span>](icordebugclass-getmodule-method.md)|<span data-ttu-id="b2888-109">Bu sınıfı tanımlayan modülü alır.</span><span class="sxs-lookup"><span data-stu-id="b2888-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="b2888-110">GetStaticFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2888-110">GetStaticFieldValue Method</span></span>](icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="b2888-111">Belirtilen statik alanın değerini alır.</span><span class="sxs-lookup"><span data-stu-id="b2888-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="b2888-112">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2888-112">GetToken Method</span></span>](icordebugclass-gettoken-method.md)|<span data-ttu-id="b2888-113">Bu sınıf için `TypeDef` meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="b2888-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2888-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2888-114">Remarks</span></span>  
 <span data-ttu-id="b2888-115">`ICorDebugClass` arabirimi örneği oluşturulmuş bir genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b2888-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="b2888-116">ICorDebugType arabirimi bir örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b2888-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="b2888-117">Örneğin, `Hashtable<K, V>` `ICorDebugClass`tarafından temsil edilir, ancak `Hashtable<Int32, String>` `ICorDebugType`tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="b2888-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="b2888-118">Genel olmayan türler hem `ICorDebugClass` hem de `ICorDebugType`ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="b2888-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="b2888-119">İkinci arabirim, tür örneği oluşturma ile başa çıkmak için .NET Framework sürüm 2,0 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="b2888-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2888-120">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="b2888-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2888-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2888-121">Requirements</span></span>  
 <span data-ttu-id="b2888-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2888-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2888-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b2888-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2888-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b2888-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2888-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2888-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2888-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2888-126">See also</span></span>

- [<span data-ttu-id="b2888-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b2888-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
