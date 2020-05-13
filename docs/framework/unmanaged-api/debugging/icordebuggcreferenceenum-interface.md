---
title: ICorDebugGCReferenceEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
ms.openlocfilehash: 5650a7e6e6cb0108f0d043914ea94debe2b703bf
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213107"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="c28bf-102">ICorDebugGCReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c28bf-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="c28bf-103">Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c28bf-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c28bf-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c28bf-104">Methods</span></span>  
  
|<span data-ttu-id="c28bf-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c28bf-105">Method</span></span>|<span data-ttu-id="c28bf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c28bf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c28bf-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c28bf-107">Next Method</span></span>](icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="c28bf-108">Atık olarak toplanabilecek nesneler hakkında bilgi içeren [cor_gc_reference](cor-gc-reference-structure.md) örneklerinin belirtilen sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c28bf-108">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c28bf-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c28bf-109">Remarks</span></span>  
 <span data-ttu-id="c28bf-110">`ICorDebugGCReferenceEnum`Arabirim "ıcorhata ayıklama Genum" arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="c28bf-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="c28bf-111">`ICorDebugGCReferenceEnum` [ICorDebugProcess5:: EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) yöntemi çağırarak bir örnek [cor_gc_reference](cor-gc-reference-structure.md) örneklerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="c28bf-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="c28bf-112">[Cor_gc_reference](cor-gc-reference-structure.md) nesneler [ıcorıtcggcreference:: Next](icordebuggcreferenceenum-next-method.md) yöntemi çağırarak Numaralandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c28bf-112">[COR_GC_REFERENCE](cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="c28bf-113">Bu yöntem tarafından doldurulan koleksiyondaki [cor_gc_reference](cor-gc-reference-structure.md) nesneleri üç tür nesneyi temsil eder:</span><span class="sxs-lookup"><span data-stu-id="c28bf-113">The [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="c28bf-114">Tüm yönetilen yığınlardan nesneler.</span><span class="sxs-lookup"><span data-stu-id="c28bf-114">Objects from all managed stacks.</span></span> <span data-ttu-id="c28bf-115">Bu, Yönetilen koddaki canlı başvuruları ve ortak dil çalışma zamanı tarafından oluşturulan nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c28bf-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="c28bf-116">Tanıtıcı tablodaki nesneler.</span><span class="sxs-lookup"><span data-stu-id="c28bf-116">Objects from the handle table.</span></span> <span data-ttu-id="c28bf-117">Bu, bir modüldeki tanımlayıcı başvuruları ( `HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT` ) ve statik değişkenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c28bf-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="c28bf-118">Sonlandırıcı sırasından nesneler.</span><span class="sxs-lookup"><span data-stu-id="c28bf-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="c28bf-119">Sonlandırıcı, Sonlandırıcı çalıştırılıncaya kadar kök nesneleri kuyruğa al.</span><span class="sxs-lookup"><span data-stu-id="c28bf-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c28bf-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c28bf-120">Requirements</span></span>  
 <span data-ttu-id="c28bf-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c28bf-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c28bf-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c28bf-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c28bf-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c28bf-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c28bf-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c28bf-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c28bf-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c28bf-125">See also</span></span>

- [<span data-ttu-id="c28bf-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c28bf-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
