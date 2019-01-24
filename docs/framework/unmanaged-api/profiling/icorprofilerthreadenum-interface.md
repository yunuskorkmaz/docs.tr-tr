---
title: ICorProfilerThreadEnum Arabirimi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd7d5f66ef7c8f2b36b8dcb725b1931993c118dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526398"
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="2c2ec-102">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c2ec-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="2c2ec-103">Ortak dil çalışma zamanı iş parçacıklarının koleksiyonunu sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c2ec-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c2ec-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2c2ec-104">Methods</span></span>  
  
|<span data-ttu-id="2c2ec-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2c2ec-105">Method</span></span>|<span data-ttu-id="2c2ec-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c2ec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c2ec-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c2ec-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="2c2ec-108">Bu bir kopyasını bir arabirim işaretçisi alır `ICorProfilerThreadEnum` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="2c2ec-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="2c2ec-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c2ec-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="2c2ec-110">Uygulama tarafından kullanılan iş parçacıklarının sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="2c2ec-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="2c2ec-111">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c2ec-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|<span data-ttu-id="2c2ec-112">İş parçacıkları Numaralandırıcının dizideki geçerli konum başlayarak, sıralı bir koleksiyonu belirtilen bitişik iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="2c2ec-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="2c2ec-113">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c2ec-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="2c2ec-114">Numaralandırıcının imleç dizisi başlangıç konumuna gider.</span><span class="sxs-lookup"><span data-stu-id="2c2ec-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="2c2ec-115">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c2ec-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="2c2ec-116">Numaralandırıcının imleç belirtilen sayıda öğeyi atlamak için geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="2c2ec-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c2ec-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c2ec-117">Remarks</span></span>  
 <span data-ttu-id="2c2ec-118">`ICorProfilerThreadEnum` Arabirimidir bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="2c2ec-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="2c2ec-119">Dizi alıcı, alıcının uygun bir hızda gönderenden çekme öğelerine sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c2ec-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="2c2ec-120">Diğer bir deyişle, böylece büyük diziler yöntemi parametre olarak geçirmeyi ile ilgili sorunları önleme açıkça dizi öğeleri akışını denetlemek için alıcıdır.</span><span class="sxs-lookup"><span data-stu-id="2c2ec-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c2ec-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c2ec-121">Requirements</span></span>  
 <span data-ttu-id="2c2ec-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c2ec-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c2ec-123">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2c2ec-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c2ec-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c2ec-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c2ec-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c2ec-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c2ec-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c2ec-126">See also</span></span>
- [<span data-ttu-id="2c2ec-127">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c2ec-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="2c2ec-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2c2ec-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
