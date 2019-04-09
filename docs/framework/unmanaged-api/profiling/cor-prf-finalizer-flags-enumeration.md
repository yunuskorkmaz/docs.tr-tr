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
ms.openlocfilehash: d5037f335e8d66c341d70d91d955a1ac7571b823
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123766"
---
# <a name="corprffinalizerflags-enumeration"></a><span data-ttu-id="934b3-102">COR_PRF_FINALIZER_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="934b3-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="934b3-103">Bir nesnenin Sonlandırıcısı açıklar.</span><span class="sxs-lookup"><span data-stu-id="934b3-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="934b3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="934b3-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="934b3-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="934b3-105">Members</span></span>  
  
|<span data-ttu-id="934b3-106">Üye</span><span class="sxs-lookup"><span data-stu-id="934b3-106">Member</span></span>|<span data-ttu-id="934b3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="934b3-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="934b3-108">Sonlandırıcı büyük/küçük harf önemlidir.</span><span class="sxs-lookup"><span data-stu-id="934b3-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="934b3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="934b3-109">Remarks</span></span>  
 <span data-ttu-id="934b3-110">`COR_PRF_FINALIZER_FLAGS` Numaralandırması tarafından kullanılan [Icorprofilercallback2::finalizeableobjectqueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) nesnenin Sonlandırıcısı açıklamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="934b3-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="934b3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="934b3-111">Requirements</span></span>  
 <span data-ttu-id="934b3-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="934b3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="934b3-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="934b3-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="934b3-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="934b3-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="934b3-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="934b3-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="934b3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="934b3-116">See also</span></span>

- [<span data-ttu-id="934b3-117">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="934b3-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
