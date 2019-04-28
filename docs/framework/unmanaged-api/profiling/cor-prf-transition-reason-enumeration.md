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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599045"
---
# <a name="corprftransitionreason-enumeration"></a><span data-ttu-id="474c2-102">COR_PRF_TRANSITION_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="474c2-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="474c2-103">Yönetilmeyen kod veya tam tersi yönetilen bir geçiş nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="474c2-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="474c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="474c2-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="474c2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="474c2-105">Members</span></span>  
  
|<span data-ttu-id="474c2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="474c2-106">Member</span></span>|<span data-ttu-id="474c2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="474c2-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="474c2-108">Bir işlev çağrısını geçiş kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="474c2-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="474c2-109">Bir işlevden bir dönüş geçiş kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="474c2-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="474c2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="474c2-110">Remarks</span></span>  
 <span data-ttu-id="474c2-111">Bir geçiş oluştuğunda, profil oluşturucuyu alır bir [Icorprofilercallback::managedtounmanagedtransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) veya [Icorprofilercallback::unmanagedtomanagedtransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) geri çağırma, bunların değerini sağlar `COR_PRF_TRANSITION_REASON` geçişin nedenini belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="474c2-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="474c2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="474c2-112">Requirements</span></span>  
 <span data-ttu-id="474c2-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="474c2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="474c2-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="474c2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="474c2-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="474c2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="474c2-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="474c2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
