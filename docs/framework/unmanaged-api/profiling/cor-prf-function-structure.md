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
ms.openlocfilehash: 1da8f414ccf0c1eed3ec7dde842dd381440a3fa9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674963"
---
# <a name="cor_prf_function-structure"></a><span data-ttu-id="3eb34-102">COR_PRF_FUNCTION Yapısı</span><span class="sxs-lookup"><span data-stu-id="3eb34-102">COR_PRF_FUNCTION Structure</span></span>

<span data-ttu-id="3eb34-103">, KIMLIĞINI yeniden derlenmesi sürümünün KIMLIĞIYLE birleştirerek bir işlevin benzersiz bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3eb34-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eb34-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3eb34-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="3eb34-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3eb34-105">Members</span></span>  
  
|<span data-ttu-id="3eb34-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3eb34-106">Member</span></span>|<span data-ttu-id="3eb34-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3eb34-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="3eb34-108">İşlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="3eb34-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="3eb34-109">Yeniden derlenen işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="3eb34-109">The ID of the recompiled function.</span></span> <span data-ttu-id="3eb34-110">0 (sıfır) değeri, işlevin orijinal sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3eb34-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3eb34-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3eb34-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eb34-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3eb34-112">Requirements</span></span>  

 <span data-ttu-id="3eb34-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3eb34-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eb34-114">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="3eb34-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3eb34-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3eb34-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3eb34-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eb34-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb34-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3eb34-117">See also</span></span>

- [<span data-ttu-id="3eb34-118">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="3eb34-118">Profiling Structures</span></span>](profiling-structures.md)
