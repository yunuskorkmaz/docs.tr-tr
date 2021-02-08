---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıtcggcreferenceenum arabirimi'
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
ms.openlocfilehash: ad4a61cdc2b30fb4c8e2be500eae878327c6b449
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801299"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="b0b26-103">ICorDebugGCReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0b26-103">ICorDebugGCReferenceEnum Interface</span></span>

<span data-ttu-id="b0b26-104">Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0b26-104">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0b26-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b0b26-105">Methods</span></span>  
  
|<span data-ttu-id="b0b26-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b0b26-106">Method</span></span>|<span data-ttu-id="b0b26-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0b26-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0b26-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0b26-108">Next Method</span></span>](icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="b0b26-109">Atık olarak toplanabilecek nesneler hakkında bilgi içeren [cor_gc_reference](cor-gc-reference-structure.md) örneklerinin belirtilen sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="b0b26-109">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0b26-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0b26-110">Remarks</span></span>  

 <span data-ttu-id="b0b26-111">`ICorDebugGCReferenceEnum`Arabirim "ıcorhata ayıklama Genum" arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="b0b26-111">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="b0b26-112">`ICorDebugGCReferenceEnum` [ICorDebugProcess5:: EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) yöntemi çağırarak bir örnek [cor_gc_reference](cor-gc-reference-structure.md) örneklerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="b0b26-112">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="b0b26-113">[Cor_gc_reference](cor-gc-reference-structure.md) nesneler [ıcorıtcggcreference:: Next](icordebuggcreferenceenum-next-method.md) yöntemi çağırarak Numaralandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b0b26-113">[COR_GC_REFERENCE](cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="b0b26-114">Bu yöntem tarafından doldurulan koleksiyondaki [cor_gc_reference](cor-gc-reference-structure.md) nesneleri üç tür nesneyi temsil eder:</span><span class="sxs-lookup"><span data-stu-id="b0b26-114">The [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="b0b26-115">Tüm yönetilen yığınlardan nesneler.</span><span class="sxs-lookup"><span data-stu-id="b0b26-115">Objects from all managed stacks.</span></span> <span data-ttu-id="b0b26-116">Bu, Yönetilen koddaki canlı başvuruları ve ortak dil çalışma zamanı tarafından oluşturulan nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b0b26-116">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="b0b26-117">Tanıtıcı tablodaki nesneler.</span><span class="sxs-lookup"><span data-stu-id="b0b26-117">Objects from the handle table.</span></span> <span data-ttu-id="b0b26-118">Bu, bir modüldeki tanımlayıcı başvuruları ( `HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT` ) ve statik değişkenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b0b26-118">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="b0b26-119">Sonlandırıcı sırasından nesneler.</span><span class="sxs-lookup"><span data-stu-id="b0b26-119">Objects from the finalizer queue.</span></span> <span data-ttu-id="b0b26-120">Sonlandırıcı, Sonlandırıcı çalıştırılıncaya kadar kök nesneleri kuyruğa al.</span><span class="sxs-lookup"><span data-stu-id="b0b26-120">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0b26-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0b26-121">Requirements</span></span>  

 <span data-ttu-id="b0b26-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0b26-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0b26-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b0b26-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0b26-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b0b26-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0b26-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0b26-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0b26-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0b26-126">See also</span></span>

- [<span data-ttu-id="b0b26-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b0b26-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
