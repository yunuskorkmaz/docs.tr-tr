---
title: COR_PRF_EX_CLAUSE_INFO Yapısı
ms.date: 03/30/2017
api_name:
- COR_PRF_EX_CLAUSE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords:
- COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e12410ab9886055dca8c3f9103c1e56475c2d5e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140354"
---
# <a name="corprfexclauseinfo-structure"></a><span data-ttu-id="630d5-102">COR_PRF_EX_CLAUSE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="630d5-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="630d5-103">Bir özel durum yan tümcesi örneği ve ilişkili çerçevesini hakkındaki bilgileri saklar.</span><span class="sxs-lookup"><span data-stu-id="630d5-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="630d5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="630d5-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="630d5-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="630d5-105">Members</span></span>  
  
|<span data-ttu-id="630d5-106">Üye</span><span class="sxs-lookup"><span data-stu-id="630d5-106">Member</span></span>|<span data-ttu-id="630d5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="630d5-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="630d5-108">Değerini [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) özel durum yan tümcesi yalnızca girilen kod veya sol türünü belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="630d5-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="630d5-109">Yerel giriş noktası yan tümcesi işleyicisinin — Örneğin, X86 EIP kaydının içeriğini.</span><span class="sxs-lookup"><span data-stu-id="630d5-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="630d5-110">Yan tümcesi işleyicisi için mantıksal çerçeve işaretçisi — Örneğin, X86 EBP kaydının içeriğini.</span><span class="sxs-lookup"><span data-stu-id="630d5-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="630d5-111">Gölge yığın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="630d5-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="630d5-112">Bu değer BSP kaydının içeriğini ve yalnızca IA64 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="630d5-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="630d5-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="630d5-113">Remarks</span></span>  
 <span data-ttu-id="630d5-114">Bir özel durum bildirimi alındığında [Icorprofilerınfo2::getnotifiedexceptionclauseınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) özel durum yan tümcesinin yerel adres ve çerçeve bilgilerini almak için kullanılabilir (`catch` / `finally`/filtreleme) hakkında çalıştırılacak veya yalnızca çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="630d5-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="630d5-115">Bu geri aramalarda ortak dil çalışma zamanının (CLR) yürütme bir özel durum yan tümcesinin içerir:</span><span class="sxs-lookup"><span data-stu-id="630d5-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
-   [<span data-ttu-id="630d5-116">Icorprofilercallback::exceptioncatcherenter</span><span class="sxs-lookup"><span data-stu-id="630d5-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
-   [<span data-ttu-id="630d5-117">Icorprofilercallback::exceptionunwindfinallyenter</span><span class="sxs-lookup"><span data-stu-id="630d5-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
-   [<span data-ttu-id="630d5-118">Icorprofilercallback::exceptionsearchfilterenter</span><span class="sxs-lookup"><span data-stu-id="630d5-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
-   [<span data-ttu-id="630d5-119">Icorprofilercallback::exceptioncatcherleave</span><span class="sxs-lookup"><span data-stu-id="630d5-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
-   [<span data-ttu-id="630d5-120">Icorprofilercallback::exceptionunwindfinallyleave</span><span class="sxs-lookup"><span data-stu-id="630d5-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
-   [<span data-ttu-id="630d5-121">Icorprofilercallback::exceptionsearchfilterleave</span><span class="sxs-lookup"><span data-stu-id="630d5-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="630d5-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="630d5-122">Requirements</span></span>  
 <span data-ttu-id="630d5-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="630d5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="630d5-124">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="630d5-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="630d5-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="630d5-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="630d5-126">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="630d5-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="630d5-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="630d5-127">See also</span></span>

- [<span data-ttu-id="630d5-128">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="630d5-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
