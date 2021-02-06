---
description: 'Daha fazla bilgi edinin: COR_PRF_FUNCTION yapısı'
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
ms.openlocfilehash: 494f3cfe6d1e3641645ef0050c06014e67bf4475
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648980"
---
# <a name="cor_prf_function-structure"></a><span data-ttu-id="ee6ca-103">COR_PRF_FUNCTION Yapısı</span><span class="sxs-lookup"><span data-stu-id="ee6ca-103">COR_PRF_FUNCTION Structure</span></span>

<span data-ttu-id="ee6ca-104">, KIMLIĞINI yeniden derlenmesi sürümünün KIMLIĞIYLE birleştirerek bir işlevin benzersiz bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee6ca-104">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee6ca-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ee6ca-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="ee6ca-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ee6ca-106">Members</span></span>  
  
|<span data-ttu-id="ee6ca-107">Üye</span><span class="sxs-lookup"><span data-stu-id="ee6ca-107">Member</span></span>|<span data-ttu-id="ee6ca-108">Description</span><span class="sxs-lookup"><span data-stu-id="ee6ca-108">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="ee6ca-109">İşlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="ee6ca-109">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="ee6ca-110">Yeniden derlenen işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="ee6ca-110">The ID of the recompiled function.</span></span> <span data-ttu-id="ee6ca-111">0 (sıfır) değeri, işlevin orijinal sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee6ca-111">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee6ca-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee6ca-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee6ca-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee6ca-113">Requirements</span></span>  

 <span data-ttu-id="ee6ca-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee6ca-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee6ca-115">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="ee6ca-115">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ee6ca-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ee6ca-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee6ca-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee6ca-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee6ca-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee6ca-118">See also</span></span>

- [<span data-ttu-id="ee6ca-119">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="ee6ca-119">Profiling Structures</span></span>](profiling-structures.md)
