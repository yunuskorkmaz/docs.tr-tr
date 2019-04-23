---
title: COR_PRF_FUNCTION Yapısı
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION
helpviewer_keywords:
- COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14d42a4032c3e2b1c231414678912e1658e759d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101731"
---
# <a name="corprffunction-structure"></a><span data-ttu-id="a6cae-102">COR_PRF_FUNCTION Yapısı</span><span class="sxs-lookup"><span data-stu-id="a6cae-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="a6cae-103">Znovu sürümü kimliği Kimliğini birleştirerek bir işlev benzersiz bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6cae-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6cae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6cae-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="a6cae-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a6cae-105">Members</span></span>  
  
|<span data-ttu-id="a6cae-106">Üye</span><span class="sxs-lookup"><span data-stu-id="a6cae-106">Member</span></span>|<span data-ttu-id="a6cae-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6cae-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="a6cae-108">İşlev kimliği.</span><span class="sxs-lookup"><span data-stu-id="a6cae-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="a6cae-109">Znovu işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="a6cae-109">The ID of the recompiled function.</span></span> <span data-ttu-id="a6cae-110">0 (sıfır) değerini işlevi orijinal sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a6cae-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6cae-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6cae-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6cae-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6cae-112">Requirements</span></span>  
 <span data-ttu-id="a6cae-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6cae-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6cae-114">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="a6cae-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a6cae-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6cae-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6cae-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6cae-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6cae-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6cae-117">See also</span></span>

- [<span data-ttu-id="a6cae-118">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="a6cae-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
