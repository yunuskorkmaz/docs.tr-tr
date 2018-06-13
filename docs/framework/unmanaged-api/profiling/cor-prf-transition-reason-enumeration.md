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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2556196b7c8f81709e6880962e8ff36e126dd8b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450069"
---
# <a name="corprftransitionreason-enumeration"></a><span data-ttu-id="1913d-102">COR_PRF_TRANSITION_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="1913d-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="1913d-103">Yönetilmeyen kod için veya tersi yönetilen bir geçiş nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1913d-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1913d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1913d-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="1913d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1913d-105">Members</span></span>  
  
|<span data-ttu-id="1913d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1913d-106">Member</span></span>|<span data-ttu-id="1913d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1913d-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="1913d-108">Bir işlev çağrısını geçişi kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="1913d-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="1913d-109">Geçiş işlevi bir dönüş kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="1913d-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1913d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1913d-110">Remarks</span></span>  
 <span data-ttu-id="1913d-111">Bir geçiş gerçekleştiğinde, profil oluşturucu aldığı bir [Icorprofilercallback::managedtounmanagedtransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) veya [Icorprofilercallback::unmanagedtomanagedtransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) geri arama, aşağıdakilerden biri değerini sağlar `COR_PRF_TRANSITION_REASON` geçişin nedenini belirtmek için numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="1913d-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1913d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1913d-112">Requirements</span></span>  
 <span data-ttu-id="1913d-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1913d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1913d-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1913d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1913d-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1913d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1913d-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1913d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
