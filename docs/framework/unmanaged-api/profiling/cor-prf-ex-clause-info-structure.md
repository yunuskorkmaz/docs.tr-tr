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
ms.openlocfilehash: fb6d2e5fc21047fea0928137f983c553f9bb2bbd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867288"
---
# <a name="cor_prf_ex_clause_info-structure"></a><span data-ttu-id="0c800-102">COR_PRF_EX_CLAUSE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="0c800-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="0c800-103">Belirli bir özel durum yan tümcesi ve onunla ilişkili çerçevesini hakkında bilgi depolar.</span><span class="sxs-lookup"><span data-stu-id="0c800-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c800-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c800-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="0c800-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0c800-105">Members</span></span>  
  
|<span data-ttu-id="0c800-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0c800-106">Member</span></span>|<span data-ttu-id="0c800-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c800-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="0c800-108">Yeni girilen veya soldaki kodun özel durum yan tümcesinin türünü belirten [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="0c800-108">A value of the [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="0c800-109">Yan tümce işleyicisinin yerel giriş noktası — Örneğin, x86 EıP kaydının içeriği.</span><span class="sxs-lookup"><span data-stu-id="0c800-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="0c800-110">Yan tümce işleyicisi için mantıksal çerçeveye yönelik işaretçi — Örneğin, x86 EBP kaydının içeriği.</span><span class="sxs-lookup"><span data-stu-id="0c800-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="0c800-111">Gölge yığınının işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0c800-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="0c800-112">Bu değer BSP yazmacın içerikleri ve yalnızca ıA64 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0c800-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c800-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c800-113">Remarks</span></span>  
 <span data-ttu-id="0c800-114">Bir özel durum bildirimi alındığında, [ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) , çalıştırılmak üzere veya yalnızca çalıştırılmış olan özel durum yan tümcesinin (`catch`/`finally`/Filter) yerel adresini ve çerçeve bilgilerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c800-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="0c800-115">Özel durum yan tümcesinin yürütülmesi, ortak dil çalışma zamanından (CLR) bu geri çağırmaları içerir:</span><span class="sxs-lookup"><span data-stu-id="0c800-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="0c800-116">ICorProfilerCallback:: ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="0c800-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="0c800-117">ICorProfilerCallback:: Exceptionunwınbir Finallyenter</span><span class="sxs-lookup"><span data-stu-id="0c800-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="0c800-118">ICorProfilerCallback:: ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="0c800-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="0c800-119">ICorProfilerCallback:: Exceptioncatch Erleave</span><span class="sxs-lookup"><span data-stu-id="0c800-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="0c800-120">ICorProfilerCallback:: Exceptionunwınbir Finallyleave</span><span class="sxs-lookup"><span data-stu-id="0c800-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="0c800-121">ICorProfilerCallback:: ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="0c800-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="0c800-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c800-122">Requirements</span></span>  
 <span data-ttu-id="0c800-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c800-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c800-124">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="0c800-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="0c800-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0c800-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c800-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c800-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c800-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c800-127">See also</span></span>

- [<span data-ttu-id="0c800-128">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="0c800-128">Profiling Structures</span></span>](profiling-structures.md)
