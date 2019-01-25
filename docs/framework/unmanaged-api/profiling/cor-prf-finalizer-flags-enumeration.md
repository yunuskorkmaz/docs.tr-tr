---
title: COR_PRF_FINALIZER_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_FINALIZER_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FINALIZER_FLAGS
helpviewer_keywords:
- COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7800567f51196154f49c93dbbbe819f77cefdfe8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499044"
---
# <a name="corprffinalizerflags-enumeration"></a><span data-ttu-id="2783e-102">COR_PRF_FINALIZER_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2783e-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="2783e-103">Bir nesnenin Sonlandırıcısı açıklar.</span><span class="sxs-lookup"><span data-stu-id="2783e-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2783e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2783e-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="2783e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2783e-105">Members</span></span>  
  
|<span data-ttu-id="2783e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2783e-106">Member</span></span>|<span data-ttu-id="2783e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2783e-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="2783e-108">Sonlandırıcı büyük/küçük harf önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2783e-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2783e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2783e-109">Remarks</span></span>  
 <span data-ttu-id="2783e-110">`COR_PRF_FINALIZER_FLAGS` Numaralandırması tarafından kullanılan [Icorprofilercallback2::finalizeableobjectqueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) nesnenin Sonlandırıcısı açıklamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2783e-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2783e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2783e-111">Requirements</span></span>  
 <span data-ttu-id="2783e-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2783e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2783e-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2783e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2783e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2783e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2783e-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2783e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2783e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2783e-116">See also</span></span>
- [<span data-ttu-id="2783e-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="2783e-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
