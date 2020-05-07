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
ms.openlocfilehash: d7417e8dc193172c77d23fe3fa72c8298d802b5c
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894037"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="9326d-102">ICorDebugClass Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9326d-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="9326d-103">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9326d-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="9326d-104">Tür geneldir ise, `ICorDebugClass` örneklenmemiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9326d-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9326d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9326d-105">Methods</span></span>  
  
|<span data-ttu-id="9326d-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9326d-106">Method</span></span>|<span data-ttu-id="9326d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9326d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9326d-108">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9326d-108">GetModule Method</span></span>](icordebugclass-getmodule-method.md)|<span data-ttu-id="9326d-109">Bu sınıfı tanımlayan modülü alır.</span><span class="sxs-lookup"><span data-stu-id="9326d-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="9326d-110">GetStaticFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9326d-110">GetStaticFieldValue Method</span></span>](icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="9326d-111">Belirtilen statik alanın değerini alır.</span><span class="sxs-lookup"><span data-stu-id="9326d-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="9326d-112">GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="9326d-112">GetToken Method</span></span>](icordebugclass-gettoken-method.md)|<span data-ttu-id="9326d-113">Bu sınıf `TypeDef` için meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="9326d-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9326d-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9326d-114">Remarks</span></span>  
 <span data-ttu-id="9326d-115">Arabirim `ICorDebugClass` , örneği oluşturulmuş bir genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9326d-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="9326d-116">ICorDebugType arabirimi bir örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9326d-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="9326d-117">Örneğin, `Hashtable<K, V>` tarafından `ICorDebugClass`temsil edilir, ancak `Hashtable<Int32, String>` tarafından `ICorDebugType`temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="9326d-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="9326d-118">Genel olmayan türler hem hem de `ICorDebugClass` ile temsil edilir `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="9326d-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="9326d-119">İkinci arabirim, tür örneği oluşturma ile başa çıkmak için .NET Framework sürüm 2,0 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="9326d-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9326d-120">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="9326d-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9326d-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9326d-121">Requirements</span></span>  
 <span data-ttu-id="9326d-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9326d-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9326d-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9326d-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9326d-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9326d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9326d-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9326d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9326d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9326d-126">See also</span></span>

- [<span data-ttu-id="9326d-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9326d-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
