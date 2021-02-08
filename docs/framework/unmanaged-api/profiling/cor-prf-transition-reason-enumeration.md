---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_TRANSITION_REASON numaralandırması'
title: COR_PRF_TRANSITION_REASON Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_TRANSITION_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_TRANSITION_REASON
helpviewer_keywords:
- COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type:
- apiref
ms.openlocfilehash: 8d0b7852f80f80a47f910e9f1240a5315772cd23
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789001"
---
# <a name="cor_prf_transition_reason-enumeration"></a><span data-ttu-id="e3a70-103">COR_PRF_TRANSITION_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e3a70-103">COR_PRF_TRANSITION_REASON Enumeration</span></span>

<span data-ttu-id="e3a70-104">Yönetilmesinin yönetilmeyen koda veya tam tersi bir geçişin sebebini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3a70-104">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3a70-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e3a70-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="e3a70-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e3a70-106">Members</span></span>  
  
|<span data-ttu-id="e3a70-107">Üye</span><span class="sxs-lookup"><span data-stu-id="e3a70-107">Member</span></span>|<span data-ttu-id="e3a70-108">Description</span><span class="sxs-lookup"><span data-stu-id="e3a70-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="e3a70-109">Geçiş bir işleve yapılan çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="e3a70-109">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="e3a70-110">Geçiş, bir işlevden geri dönüş nedeniyle yapılır.</span><span class="sxs-lookup"><span data-stu-id="e3a70-110">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3a70-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3a70-111">Remarks</span></span>  

 <span data-ttu-id="e3a70-112">Bir geçiş gerçekleştiğinde, profil oluşturucu bir [ICorProfilerCallback:: ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) veya [ICorProfilerCallback:: UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) geri çağırması alır, bunlardan biri, `COR_PRF_TRANSITION_REASON` geçişin nedenini göstermek için bir numaralandırma değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3a70-112">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3a70-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3a70-113">Requirements</span></span>  

 <span data-ttu-id="e3a70-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3a70-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3a70-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e3a70-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e3a70-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e3a70-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3a70-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3a70-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
