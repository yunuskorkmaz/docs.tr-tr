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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ddd8e86b119a3c19417306dee056e435a4f5d07a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537913"
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="7a335-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="7a335-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="7a335-103">İşlev bağımsız değişkenleri bitişik bellek sırayla soldan sağa depolanan bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7a335-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a335-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a335-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="7a335-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7a335-105">Members</span></span>  
  
|<span data-ttu-id="7a335-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7a335-106">Members</span></span>|<span data-ttu-id="7a335-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a335-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="7a335-108">Bloğun başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="7a335-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="7a335-109">Bitişik blok uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="7a335-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a335-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a335-110">Requirements</span></span>  
 <span data-ttu-id="7a335-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a335-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a335-112">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="7a335-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7a335-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a335-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a335-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a335-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a335-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a335-115">See also</span></span>
- [<span data-ttu-id="7a335-116">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="7a335-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
