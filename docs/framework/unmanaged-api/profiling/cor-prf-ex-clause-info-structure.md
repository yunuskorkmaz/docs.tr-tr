---
title: "COR_PRF_EX_CLAUSE_INFO Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_EX_CLAUSE_INFO
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords: COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65025384aa94ac363336bae7f37f8ea88a3bab67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corprfexclauseinfo-structure"></a><span data-ttu-id="54ef3-102">COR_PRF_EX_CLAUSE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="54ef3-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="54ef3-103">Bir özel durum yan tümcesi örneği ve ilişkili çerçevesini ilgili bilgileri depolar.</span><span class="sxs-lookup"><span data-stu-id="54ef3-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54ef3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54ef3-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="54ef3-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="54ef3-105">Members</span></span>  
  
|<span data-ttu-id="54ef3-106">Üye</span><span class="sxs-lookup"><span data-stu-id="54ef3-106">Member</span></span>|<span data-ttu-id="54ef3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54ef3-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="54ef3-108">Değerini [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) numaralandırma özel durum yan tümcesi yalnızca girilen kod veya sol türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="54ef3-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="54ef3-109">Yerel giriş noktası yan tümcesi işleyicisinin — Örneğin, X86 EIP kayıt içeriği.</span><span class="sxs-lookup"><span data-stu-id="54ef3-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="54ef3-110">Yan tümcesi işleyici mantıksal çerçeve işaretçisi — Örneğin, X86 EBP kayıt içeriği.</span><span class="sxs-lookup"><span data-stu-id="54ef3-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="54ef3-111">Gölge yığınına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="54ef3-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="54ef3-112">Bu değer BSP kayıt, içeriği ve yalnızca IA64 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="54ef3-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54ef3-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54ef3-113">Remarks</span></span>  
 <span data-ttu-id="54ef3-114">Bir özel durum bildirimi alındığında [Icorprofilerınfo2::getnotifiedexceptionclauseınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) özel durum yan tümcesinin yerel adres ve çerçeve bilgilerini almak için kullanılan (`catch` / `finally`/filtre) hakkında çalıştırılacak veya yalnızca çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="54ef3-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="54ef3-115">Özel durum yan tümcesinin yürütme bu geri aramalar ortak dil çalışma zamanı (CLR) gelen içerir:</span><span class="sxs-lookup"><span data-stu-id="54ef3-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
-   [<span data-ttu-id="54ef3-116">Icorprofilercallback::exceptioncatcherenter</span><span class="sxs-lookup"><span data-stu-id="54ef3-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
-   [<span data-ttu-id="54ef3-117">Icorprofilercallback::exceptionunwindfinallyenter</span><span class="sxs-lookup"><span data-stu-id="54ef3-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
-   [<span data-ttu-id="54ef3-118">Icorprofilercallback::exceptionsearchfilterenter</span><span class="sxs-lookup"><span data-stu-id="54ef3-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
-   [<span data-ttu-id="54ef3-119">Icorprofilercallback::exceptioncatcherleave</span><span class="sxs-lookup"><span data-stu-id="54ef3-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
-   [<span data-ttu-id="54ef3-120">Icorprofilercallback::exceptionunwindfinallyleave</span><span class="sxs-lookup"><span data-stu-id="54ef3-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
-   [<span data-ttu-id="54ef3-121">Icorprofilercallback::exceptionsearchfilterleave</span><span class="sxs-lookup"><span data-stu-id="54ef3-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="54ef3-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54ef3-122">Requirements</span></span>  
 <span data-ttu-id="54ef3-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54ef3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54ef3-124">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="54ef3-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="54ef3-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54ef3-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54ef3-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54ef3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54ef3-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54ef3-127">See Also</span></span>  
 [<span data-ttu-id="54ef3-128">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="54ef3-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
