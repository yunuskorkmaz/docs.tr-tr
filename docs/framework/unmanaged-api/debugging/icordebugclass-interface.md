---
title: Icordebugclass arabirimi1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d12d952fe540b2ec36d058ae2100f0cf5c8e6bcf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710234"
---
# <a name="icordebugclass-interface1"></a><span data-ttu-id="eb4a2-102">Icordebugclass arabirimi1</span><span class="sxs-lookup"><span data-stu-id="eb4a2-102">ICorDebugClass Interface1</span></span>
<span data-ttu-id="eb4a2-103">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eb4a2-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="eb4a2-104">Tür genelse, `ICorDebugClass` örneklenmemiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eb4a2-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb4a2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="eb4a2-105">Methods</span></span>  
  
|<span data-ttu-id="eb4a2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="eb4a2-106">Method</span></span>|<span data-ttu-id="eb4a2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb4a2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb4a2-108">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb4a2-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="eb4a2-109">Bu sınıfı tanımlayan modül alır.</span><span class="sxs-lookup"><span data-stu-id="eb4a2-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="eb4a2-110">GetStaticFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb4a2-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="eb4a2-111">Belirtilen statik alan değerini alır.</span><span class="sxs-lookup"><span data-stu-id="eb4a2-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="eb4a2-112">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb4a2-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="eb4a2-113">Alır `TypeDef` Bu sınıf için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="eb4a2-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb4a2-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb4a2-114">Remarks</span></span>  
 <span data-ttu-id="eb4a2-115">`ICorDebugClass` Arabirimi bir örneklenmemiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eb4a2-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="eb4a2-116">Icordebugtype arabirimi örneklenmiş bir genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eb4a2-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="eb4a2-117">Örneğin, `Hashtable<K, V>` tarafından temsil edilir `ICorDebugClass`bilgileriyse `Hashtable<Int32, String>` tarafından temsil edilir `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="eb4a2-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="eb4a2-118">Genel olmayan türler tarafından temsil edilir `ICorDebugClass` ve `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="eb4a2-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="eb4a2-119">İkinci arabirim tür örneği oluşturmada ile uğraşmak için .NET Framework sürüm 2.0 kullanılmaya başlandı.</span><span class="sxs-lookup"><span data-stu-id="eb4a2-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb4a2-120">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="eb4a2-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb4a2-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb4a2-121">Requirements</span></span>  
 <span data-ttu-id="eb4a2-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb4a2-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb4a2-123">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb4a2-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb4a2-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb4a2-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb4a2-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb4a2-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb4a2-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb4a2-126">See also</span></span>
- [<span data-ttu-id="eb4a2-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eb4a2-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
