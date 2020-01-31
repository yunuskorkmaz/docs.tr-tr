---
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
ms.openlocfilehash: 1c3c311fd431b6c0b18af3d6516973b2471cfabd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867069"
---
# <a name="cor_prf_transition_reason-enumeration"></a><span data-ttu-id="d8c84-102">COR_PRF_TRANSITION_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d8c84-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="d8c84-103">Yönetilmesinin yönetilmeyen koda veya tam tersi bir geçişin sebebini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8c84-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8c84-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8c84-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="d8c84-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d8c84-105">Members</span></span>  
  
|<span data-ttu-id="d8c84-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d8c84-106">Member</span></span>|<span data-ttu-id="d8c84-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8c84-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="d8c84-108">Geçiş bir işleve yapılan çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="d8c84-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="d8c84-109">Geçiş, bir işlevden geri dönüş nedeniyle yapılır.</span><span class="sxs-lookup"><span data-stu-id="d8c84-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8c84-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8c84-110">Remarks</span></span>  
 <span data-ttu-id="d8c84-111">Bir geçiş gerçekleştiğinde, profil oluşturucu bir [ICorProfilerCallback:: ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) veya [ICorProfilerCallback:: UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) geri çağırması alır, bunlardan biri, geçişin nedenini göstermek için `COR_PRF_TRANSITION_REASON` numaralandırması değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8c84-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8c84-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8c84-112">Requirements</span></span>  
 <span data-ttu-id="d8c84-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8c84-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8c84-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d8c84-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8c84-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d8c84-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8c84-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8c84-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
