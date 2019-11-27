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
ms.openlocfilehash: df4bfe69b22439073342693a03376a0b506f9c70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428379"
---
# <a name="cor_prf_ex_clause_info-structure"></a><span data-ttu-id="04f35-102">COR_PRF_EX_CLAUSE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="04f35-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="04f35-103">Belirli bir özel durum yan tümcesi ve onunla ilişkili çerçevesini hakkında bilgi depolar.</span><span class="sxs-lookup"><span data-stu-id="04f35-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04f35-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04f35-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="04f35-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="04f35-105">Members</span></span>  
  
|<span data-ttu-id="04f35-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="04f35-106">Member</span></span>|<span data-ttu-id="04f35-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04f35-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="04f35-108">Yeni girilen veya soldaki kodun özel durum yan tümcesinin türünü belirten [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="04f35-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="04f35-109">Yan tümce işleyicisinin yerel giriş noktası — Örneğin, x86 EıP kaydının içeriği.</span><span class="sxs-lookup"><span data-stu-id="04f35-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="04f35-110">Yan tümce işleyicisi için mantıksal çerçeveye yönelik işaretçi — Örneğin, x86 EBP kaydının içeriği.</span><span class="sxs-lookup"><span data-stu-id="04f35-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="04f35-111">Gölge yığınının işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="04f35-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="04f35-112">Bu değer BSP yazmacın içerikleri ve yalnızca ıA64 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="04f35-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04f35-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04f35-113">Remarks</span></span>  
 <span data-ttu-id="04f35-114">Bir özel durum bildirimi alındığında, [ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) , çalıştırılmak üzere veya yalnızca çalıştırılmış olan özel durum yan tümcesinin (`catch`/`finally`/Filter) yerel adresini ve çerçeve bilgilerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="04f35-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="04f35-115">Özel durum yan tümcesinin yürütülmesi, ortak dil çalışma zamanından (CLR) bu geri çağırmaları içerir:</span><span class="sxs-lookup"><span data-stu-id="04f35-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="04f35-116">ICorProfilerCallback:: ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="04f35-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="04f35-117">ICorProfilerCallback:: Exceptionunwınbir Finallyenter</span><span class="sxs-lookup"><span data-stu-id="04f35-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="04f35-118">ICorProfilerCallback:: ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="04f35-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="04f35-119">ICorProfilerCallback:: Exceptioncatch Erleave</span><span class="sxs-lookup"><span data-stu-id="04f35-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="04f35-120">ICorProfilerCallback:: Exceptionunwınbir Finallyleave</span><span class="sxs-lookup"><span data-stu-id="04f35-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="04f35-121">ICorProfilerCallback:: ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="04f35-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="04f35-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04f35-122">Requirements</span></span>  
 <span data-ttu-id="04f35-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04f35-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04f35-124">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="04f35-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="04f35-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="04f35-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04f35-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04f35-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04f35-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04f35-127">See also</span></span>

- [<span data-ttu-id="04f35-128">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="04f35-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
