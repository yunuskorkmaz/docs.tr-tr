---
title: "COR_PRF_FUNCTION_ARGUMENT_RANGE Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7f61d23fc3ee3c6c8adb46c0deecdd72d155ae65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="46eff-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="46eff-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="46eff-103">İşlev bağımsız değişkenleri bitişik bellek soldan sağa sırayla depolanan bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="46eff-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46eff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46eff-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="46eff-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="46eff-105">Members</span></span>  
  
|<span data-ttu-id="46eff-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="46eff-106">Members</span></span>|<span data-ttu-id="46eff-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46eff-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="46eff-108">Bloğun başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="46eff-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="46eff-109">Bitişik blok uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="46eff-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="46eff-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46eff-110">Requirements</span></span>  
 <span data-ttu-id="46eff-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46eff-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46eff-112">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="46eff-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="46eff-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46eff-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46eff-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46eff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46eff-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46eff-115">See Also</span></span>  
 [<span data-ttu-id="46eff-116">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="46eff-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
