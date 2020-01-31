---
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
ms.openlocfilehash: dae5ed7c25f85051d1a28681fb88b056617c4de0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867257"
---
# <a name="cor_prf_function_argument_range-structure"></a><span data-ttu-id="84321-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="84321-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="84321-103">Bitişik olarak depolanan bir işlev bağımsız değişkenlerinin bloğunu, bellekte soldan sağa doğru sırada olacak şekilde gösterir.</span><span class="sxs-lookup"><span data-stu-id="84321-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84321-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84321-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="84321-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="84321-105">Members</span></span>  
  
|<span data-ttu-id="84321-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="84321-106">Members</span></span>|<span data-ttu-id="84321-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84321-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="84321-108">Bloğun başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="84321-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="84321-109">Bitişik bloğun uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="84321-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="84321-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84321-110">Requirements</span></span>  
 <span data-ttu-id="84321-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84321-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84321-112">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="84321-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="84321-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="84321-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84321-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84321-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84321-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84321-115">See also</span></span>

- [<span data-ttu-id="84321-116">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="84321-116">Profiling Structures</span></span>](profiling-structures.md)
