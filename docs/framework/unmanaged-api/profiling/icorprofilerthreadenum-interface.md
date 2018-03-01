---
title: ICorProfilerThreadEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4758d97aab0b4827ba955922c6b14f35ff0f3f81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="57c46-102">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57c46-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="57c46-103">Ortak dil çalışma zamanı iş parçacıkları koleksiyonu sırayla yinelemek için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="57c46-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57c46-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="57c46-104">Methods</span></span>  
  
|<span data-ttu-id="57c46-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="57c46-105">Method</span></span>|<span data-ttu-id="57c46-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57c46-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57c46-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57c46-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="57c46-108">Bu bir kopyasını bir arabirim işaretçisi alır `ICorProfilerThreadEnum` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="57c46-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="57c46-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57c46-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="57c46-110">Uygulama tarafından kullanılan iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="57c46-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="57c46-111">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57c46-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|<span data-ttu-id="57c46-112">İş parçacığı, Numaralandırıcının geçerli konumu sırada başlayarak sıralı bir koleksiyonu belirtilen bitişik iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="57c46-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="57c46-113">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57c46-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="57c46-114">Numaralandırıcının imleç dizisi başlangıç konuma taşır.</span><span class="sxs-lookup"><span data-stu-id="57c46-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="57c46-115">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57c46-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="57c46-116">Numaralandırıcının imleç belirtilen sayıda öğeyi atlamak için geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="57c46-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57c46-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57c46-117">Remarks</span></span>  
 <span data-ttu-id="57c46-118">`ICorProfilerThreadEnum` Arabirimidir bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="57c46-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="57c46-119">Bir dizi alıcı, alıcının uygun bir hızda gönderenden çekme öğelerine sağlar.</span><span class="sxs-lookup"><span data-stu-id="57c46-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="57c46-120">Diğer bir deyişle, böylece büyük diziler yöntem parametreleri olarak geçirme ile ilgili sorunları önleme açıkça dizi öğeleri akışını denetlemek için alıcıdır.</span><span class="sxs-lookup"><span data-stu-id="57c46-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57c46-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57c46-121">Requirements</span></span>  
 <span data-ttu-id="57c46-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57c46-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57c46-123">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="57c46-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="57c46-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57c46-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57c46-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57c46-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c46-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57c46-126">See Also</span></span>  
 [<span data-ttu-id="57c46-127">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57c46-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="57c46-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="57c46-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
