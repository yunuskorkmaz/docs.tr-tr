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
ms.openlocfilehash: dffefedf14d5f219736e429be191021b2de7ddd2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125599"
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="34e0c-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="34e0c-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="34e0c-103">İşlev bağımsız değişkenleri bitişik bellek sırayla soldan sağa depolanan bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="34e0c-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34e0c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34e0c-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="34e0c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="34e0c-105">Members</span></span>  
  
|<span data-ttu-id="34e0c-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="34e0c-106">Members</span></span>|<span data-ttu-id="34e0c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34e0c-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="34e0c-108">Bloğun başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="34e0c-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="34e0c-109">Bitişik blok uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="34e0c-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34e0c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34e0c-110">Requirements</span></span>  
 <span data-ttu-id="34e0c-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34e0c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34e0c-112">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="34e0c-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="34e0c-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34e0c-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="34e0c-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="34e0c-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="34e0c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34e0c-115">See also</span></span>

- [<span data-ttu-id="34e0c-116">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="34e0c-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
