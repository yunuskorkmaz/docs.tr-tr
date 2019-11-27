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
ms.openlocfilehash: 40698a49ac7012c4f67eb88b1ead04c80f3dea77
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428321"
---
# <a name="cor_prf_function-structure"></a><span data-ttu-id="a315f-102">COR_PRF_FUNCTION Yapısı</span><span class="sxs-lookup"><span data-stu-id="a315f-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="a315f-103">, KIMLIĞINI yeniden derlenmesi sürümünün KIMLIĞIYLE birleştirerek bir işlevin benzersiz bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a315f-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a315f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a315f-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="a315f-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="a315f-105">Members</span></span>  
  
|<span data-ttu-id="a315f-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="a315f-106">Member</span></span>|<span data-ttu-id="a315f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a315f-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="a315f-108">İşlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a315f-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="a315f-109">Yeniden derlenen işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a315f-109">The ID of the recompiled function.</span></span> <span data-ttu-id="a315f-110">0 (sıfır) değeri, işlevin orijinal sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a315f-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a315f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a315f-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a315f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a315f-112">Requirements</span></span>  
 <span data-ttu-id="a315f-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a315f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a315f-114">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="a315f-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a315f-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a315f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a315f-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a315f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a315f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a315f-117">See also</span></span>

- [<span data-ttu-id="a315f-118">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="a315f-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
