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
ms.openlocfilehash: 9beb8930143cbb0cc7dd8dd68a65b42d92563e31
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972059"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="aeaad-102">ICorDebugClass Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aeaad-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="aeaad-103">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aeaad-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="aeaad-104">Tür genelse, `ICorDebugClass` örneklenmemiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aeaad-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aeaad-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aeaad-105">Methods</span></span>  
  
|<span data-ttu-id="aeaad-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="aeaad-106">Method</span></span>|<span data-ttu-id="aeaad-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aeaad-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aeaad-108">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeaad-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="aeaad-109">Bu sınıfı tanımlayan modül alır.</span><span class="sxs-lookup"><span data-stu-id="aeaad-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="aeaad-110">GetStaticFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeaad-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="aeaad-111">Belirtilen statik alan değerini alır.</span><span class="sxs-lookup"><span data-stu-id="aeaad-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="aeaad-112">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeaad-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="aeaad-113">Alır `TypeDef` Bu sınıf için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="aeaad-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeaad-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aeaad-114">Remarks</span></span>  
 <span data-ttu-id="aeaad-115">`ICorDebugClass` Arabirimi bir örneklenmemiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aeaad-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="aeaad-116">Icordebugtype arabirimi örneklenmiş bir genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aeaad-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="aeaad-117">Örneğin, `Hashtable<K, V>` tarafından temsil edilir `ICorDebugClass`bilgileriyse `Hashtable<Int32, String>` tarafından temsil edilir `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="aeaad-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="aeaad-118">Genel olmayan türler tarafından temsil edilir `ICorDebugClass` ve `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="aeaad-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="aeaad-119">İkinci arabirim tür örneği oluşturmada ile uğraşmak için .NET Framework sürüm 2.0 kullanılmaya başlandı.</span><span class="sxs-lookup"><span data-stu-id="aeaad-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aeaad-120">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="aeaad-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeaad-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aeaad-121">Requirements</span></span>  
 <span data-ttu-id="aeaad-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeaad-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeaad-123">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aeaad-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aeaad-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aeaad-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aeaad-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeaad-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeaad-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aeaad-126">See also</span></span>
- [<span data-ttu-id="aeaad-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aeaad-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
