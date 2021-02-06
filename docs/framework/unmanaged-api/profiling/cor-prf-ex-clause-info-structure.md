---
description: 'Daha fazla bilgi edinin: COR_PRF_EX_CLAUSE_INFO yapısı'
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
ms.openlocfilehash: af8d404e55a8996abc69923924e87c95e3c5eae8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649214"
---
# <a name="cor_prf_ex_clause_info-structure"></a><span data-ttu-id="a8cf4-103">COR_PRF_EX_CLAUSE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="a8cf4-103">COR_PRF_EX_CLAUSE_INFO Structure</span></span>

<span data-ttu-id="a8cf4-104">Belirli bir özel durum yan tümcesi ve onunla ilişkili çerçevesini hakkında bilgi depolar.</span><span class="sxs-lookup"><span data-stu-id="a8cf4-104">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8cf4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a8cf4-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="a8cf4-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a8cf4-106">Members</span></span>  
  
|<span data-ttu-id="a8cf4-107">Üye</span><span class="sxs-lookup"><span data-stu-id="a8cf4-107">Member</span></span>|<span data-ttu-id="a8cf4-108">Description</span><span class="sxs-lookup"><span data-stu-id="a8cf4-108">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="a8cf4-109">Yeni girilen veya soldaki kodun özel durum yan tümcesinin türünü belirten [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="a8cf4-109">A value of the [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="a8cf4-110">Yan tümce işleyicisinin yerel giriş noktası — Örneğin, x86 EıP kaydının içeriği.</span><span class="sxs-lookup"><span data-stu-id="a8cf4-110">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="a8cf4-111">Yan tümce işleyicisi için mantıksal çerçeveye yönelik işaretçi — Örneğin, x86 EBP kaydının içeriği.</span><span class="sxs-lookup"><span data-stu-id="a8cf4-111">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="a8cf4-112">Gölge yığınının işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a8cf4-112">The pointer to the shadow stack.</span></span> <span data-ttu-id="a8cf4-113">Bu değer BSP yazmacın içerikleri ve yalnızca ıA64 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a8cf4-113">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8cf4-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8cf4-114">Remarks</span></span>  

 <span data-ttu-id="a8cf4-115">Bir özel durum bildirimi alındığında, çalıştırılmak üzere veya yalnızca çalıştırılmış olan özel durum yan tümcesinin (/Filter) yerel adres ve çerçeve bilgilerini almak için [ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) kullanılabilir `catch` / `finally` .</span><span class="sxs-lookup"><span data-stu-id="a8cf4-115">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="a8cf4-116">Özel durum yan tümcesinin yürütülmesi, ortak dil çalışma zamanından (CLR) bu geri çağırmaları içerir:</span><span class="sxs-lookup"><span data-stu-id="a8cf4-116">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="a8cf4-117">ICorProfilerCallback:: ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="a8cf4-117">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="a8cf4-118">ICorProfilerCallback:: Exceptionunwınbir Finallyenter</span><span class="sxs-lookup"><span data-stu-id="a8cf4-118">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="a8cf4-119">ICorProfilerCallback:: ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="a8cf4-119">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="a8cf4-120">ICorProfilerCallback:: Exceptioncatch Erleave</span><span class="sxs-lookup"><span data-stu-id="a8cf4-120">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="a8cf4-121">ICorProfilerCallback:: Exceptionunwınbir Finallyleave</span><span class="sxs-lookup"><span data-stu-id="a8cf4-121">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="a8cf4-122">ICorProfilerCallback:: ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="a8cf4-122">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="a8cf4-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8cf4-123">Requirements</span></span>  

 <span data-ttu-id="a8cf4-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8cf4-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8cf4-125">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="a8cf4-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a8cf4-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a8cf4-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8cf4-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8cf4-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8cf4-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8cf4-128">See also</span></span>

- [<span data-ttu-id="a8cf4-129">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="a8cf4-129">Profiling Structures</span></span>](profiling-structures.md)
