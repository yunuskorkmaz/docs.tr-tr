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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc5099af23a2b706694bfcb655d295607c97ea8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969276"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="158a1-102">ICorDebugClass Arabirimi</span><span class="sxs-lookup"><span data-stu-id="158a1-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="158a1-103">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="158a1-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="158a1-104">Tür geneldir ise, `ICorDebugClass` örneklenmemiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="158a1-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="158a1-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="158a1-105">Methods</span></span>  
  
|<span data-ttu-id="158a1-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="158a1-106">Method</span></span>|<span data-ttu-id="158a1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="158a1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="158a1-108">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="158a1-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="158a1-109">Bu sınıfı tanımlayan modülü alır.</span><span class="sxs-lookup"><span data-stu-id="158a1-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="158a1-110">GetStaticFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="158a1-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="158a1-111">Belirtilen statik alanın değerini alır.</span><span class="sxs-lookup"><span data-stu-id="158a1-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="158a1-112">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="158a1-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="158a1-113">Bu sınıf için meta veri belirtecini alır. `TypeDef`</span><span class="sxs-lookup"><span data-stu-id="158a1-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="158a1-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="158a1-114">Remarks</span></span>  
 <span data-ttu-id="158a1-115">Arabirim `ICorDebugClass` , örneği oluşturulmuş bir genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="158a1-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="158a1-116">ICorDebugType arabirimi bir örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="158a1-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="158a1-117">Örneğin, `Hashtable<K, V>` tarafından `ICorDebugClass`temsil edilir, ancak `Hashtable<Int32, String>` tarafından `ICorDebugType`temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="158a1-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="158a1-118">Genel olmayan türler hem hem de `ICorDebugClass` `ICorDebugType`ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="158a1-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="158a1-119">İkinci arabirim, tür örneği oluşturma ile başa çıkmak için .NET Framework sürüm 2,0 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="158a1-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="158a1-120">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="158a1-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="158a1-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="158a1-121">Requirements</span></span>  
 <span data-ttu-id="158a1-122">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="158a1-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="158a1-123">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="158a1-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="158a1-124">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="158a1-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="158a1-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="158a1-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="158a1-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="158a1-126">See also</span></span>

- [<span data-ttu-id="158a1-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="158a1-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
