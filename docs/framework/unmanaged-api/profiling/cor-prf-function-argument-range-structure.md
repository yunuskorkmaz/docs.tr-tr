---
description: 'Daha fazla bilgi edinin: COR_PRF_FUNCTION_ARGUMENT_RANGE yapısı'
title: COR_PRF_FUNCTION_ARGUMENT_RANGE Yapısı
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type:
- apiref
ms.openlocfilehash: 65d762ba4513341b20426ea56d423a2066f6e714
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649032"
---
# <a name="cor_prf_function_argument_range-structure"></a><span data-ttu-id="8e0bf-103">COR_PRF_FUNCTION_ARGUMENT_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="8e0bf-103">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>

<span data-ttu-id="8e0bf-104">Bitişik olarak depolanan bir işlev bağımsız değişkenlerinin bloğunu, bellekte soldan sağa doğru sırada olacak şekilde gösterir.</span><span class="sxs-lookup"><span data-stu-id="8e0bf-104">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e0bf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8e0bf-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="8e0bf-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8e0bf-106">Members</span></span>  
  
|<span data-ttu-id="8e0bf-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8e0bf-107">Members</span></span>|<span data-ttu-id="8e0bf-108">Description</span><span class="sxs-lookup"><span data-stu-id="8e0bf-108">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="8e0bf-109">Bloğun başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="8e0bf-109">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="8e0bf-110">Bitişik bloğun uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="8e0bf-110">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8e0bf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e0bf-111">Requirements</span></span>  

 <span data-ttu-id="8e0bf-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e0bf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e0bf-113">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="8e0bf-113">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="8e0bf-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8e0bf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e0bf-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e0bf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e0bf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e0bf-116">See also</span></span>

- [<span data-ttu-id="8e0bf-117">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="8e0bf-117">Profiling Structures</span></span>](profiling-structures.md)
