---
description: ': ICorDebugClass arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5ded26a8b3a98bd273bbfe1bfa9efd1bb70d5595
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711511"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="64115-103">ICorDebugClass Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64115-103">ICorDebugClass Interface</span></span>

<span data-ttu-id="64115-104">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="64115-104">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="64115-105">Tür geneldir ise, `ICorDebugClass` örneklenmemiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="64115-105">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="64115-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="64115-106">Methods</span></span>  
  
|<span data-ttu-id="64115-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="64115-107">Method</span></span>|<span data-ttu-id="64115-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64115-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64115-109">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64115-109">GetModule Method</span></span>](icordebugclass-getmodule-method.md)|<span data-ttu-id="64115-110">Bu sınıfı tanımlayan modülü alır.</span><span class="sxs-lookup"><span data-stu-id="64115-110">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="64115-111">GetStaticFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64115-111">GetStaticFieldValue Method</span></span>](icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="64115-112">Belirtilen statik alanın değerini alır.</span><span class="sxs-lookup"><span data-stu-id="64115-112">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="64115-113">GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="64115-113">GetToken Method</span></span>](icordebugclass-gettoken-method.md)|<span data-ttu-id="64115-114">`TypeDef`Bu sınıf için meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="64115-114">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64115-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64115-115">Remarks</span></span>  

 <span data-ttu-id="64115-116">`ICorDebugClass`Arabirim, örneği oluşturulmuş bir genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="64115-116">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="64115-117">ICorDebugType arabirimi bir örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="64115-117">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="64115-118">Örneğin, tarafından temsil edilir `Hashtable<K, V>` `ICorDebugClass` , ancak `Hashtable<Int32, String>` tarafından temsil edilir `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="64115-118">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="64115-119">Genel olmayan türler hem hem de ile temsil `ICorDebugClass` edilir `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="64115-119">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="64115-120">İkinci arabirim, tür örneği oluşturma ile başa çıkmak için .NET Framework sürüm 2,0 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="64115-120">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64115-121">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="64115-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64115-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64115-122">Requirements</span></span>  

 <span data-ttu-id="64115-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64115-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64115-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="64115-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64115-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="64115-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64115-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64115-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64115-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64115-127">See also</span></span>

- [<span data-ttu-id="64115-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="64115-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
