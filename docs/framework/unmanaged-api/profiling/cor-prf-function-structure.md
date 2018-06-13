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
ms.openlocfilehash: 1bc8d588641163ccf98054fdf1930a72a04c770c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452068"
---
# <a name="corprffunction-structure"></a><span data-ttu-id="a2e2b-102">COR_PRF_FUNCTION Yapısı</span><span class="sxs-lookup"><span data-stu-id="a2e2b-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="a2e2b-103">Derlenmiş sürüm kimliği Kimliğini birleştiren bir işlev benzersiz bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2e2b-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2e2b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2e2b-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="a2e2b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a2e2b-105">Members</span></span>  
  
|<span data-ttu-id="a2e2b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="a2e2b-106">Member</span></span>|<span data-ttu-id="a2e2b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2e2b-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="a2e2b-108">İşlev kimliği.</span><span class="sxs-lookup"><span data-stu-id="a2e2b-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="a2e2b-109">Derlenmiş işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="a2e2b-109">The ID of the recompiled function.</span></span> <span data-ttu-id="a2e2b-110">0 (sıfır) değerini işlevi orijinal sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a2e2b-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2e2b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2e2b-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2e2b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2e2b-112">Requirements</span></span>  
 <span data-ttu-id="a2e2b-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2e2b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2e2b-114">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="a2e2b-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a2e2b-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2e2b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2e2b-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2e2b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e2b-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2e2b-117">See Also</span></span>  
 [<span data-ttu-id="a2e2b-118">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="a2e2b-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
