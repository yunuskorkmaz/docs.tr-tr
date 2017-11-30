---
title: Icordebugclass Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass
helpviewer_keywords: ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79e93a44f2cc532286a7e9b01fa32292a4e1c69a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugclass-interface1"></a><span data-ttu-id="37cb8-102">Icordebugclass Interface1</span><span class="sxs-lookup"><span data-stu-id="37cb8-102">ICorDebugClass Interface1</span></span>
<span data-ttu-id="37cb8-103">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="37cb8-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="37cb8-104">Tür genel, ise `ICorDebugClass` dizilerine genel türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="37cb8-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="37cb8-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="37cb8-105">Methods</span></span>  
  
|<span data-ttu-id="37cb8-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="37cb8-106">Method</span></span>|<span data-ttu-id="37cb8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37cb8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="37cb8-108">GetModule yöntemi</span><span class="sxs-lookup"><span data-stu-id="37cb8-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="37cb8-109">Bu sınıfı tanımlayan modülü alır.</span><span class="sxs-lookup"><span data-stu-id="37cb8-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="37cb8-110">GetStaticFieldValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="37cb8-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="37cb8-111">Belirtilen statik alanın değerini alır.</span><span class="sxs-lookup"><span data-stu-id="37cb8-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="37cb8-112">GetToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="37cb8-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="37cb8-113">Alır `TypeDef` Bu sınıf için meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="37cb8-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37cb8-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37cb8-114">Remarks</span></span>  
 <span data-ttu-id="37cb8-115">`ICorDebugClass` Arabirimi dizilerine genel tür temsil eder.</span><span class="sxs-lookup"><span data-stu-id="37cb8-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="37cb8-116">Icordebugtype arabirimi bir oluşturulmuş genel türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="37cb8-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="37cb8-117">Örneğin, `Hashtable<K, V>` gösterdiği `ICorDebugClass`, ancak `Hashtable<Int32, String>` gösterdiği `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="37cb8-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="37cb8-118">Olmayan genel türleri temsil edilen her ikisi için de `ICorDebugClass` ve `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="37cb8-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="37cb8-119">İkinci arabirim türü örnek oluşturma ile mücadele etmek için .NET Framework sürüm 2.0 sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="37cb8-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37cb8-120">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="37cb8-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37cb8-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37cb8-121">Requirements</span></span>  
 <span data-ttu-id="37cb8-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37cb8-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37cb8-123">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37cb8-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37cb8-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37cb8-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37cb8-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37cb8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37cb8-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37cb8-126">See Also</span></span>  
 [<span data-ttu-id="37cb8-127">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="37cb8-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
