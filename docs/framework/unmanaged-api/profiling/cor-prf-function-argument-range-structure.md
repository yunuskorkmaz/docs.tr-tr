---
title: "COR_PRF_FUNCTION_ARGUMENT_RANGE Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords: COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0c0dd9cac695d892c07f33728c22bd35102c4389
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="5454b-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="5454b-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="5454b-103">İşlev bağımsız değişkenleri bitişik bellek soldan sağa sırayla depolanan bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5454b-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5454b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5454b-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="5454b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5454b-105">Members</span></span>  
  
|<span data-ttu-id="5454b-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5454b-106">Members</span></span>|<span data-ttu-id="5454b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5454b-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="5454b-108">Bloğun başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="5454b-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="5454b-109">Bitişik blok uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="5454b-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5454b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5454b-110">Requirements</span></span>  
 <span data-ttu-id="5454b-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5454b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5454b-112">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="5454b-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="5454b-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5454b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5454b-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5454b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5454b-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5454b-115">See Also</span></span>  
 [<span data-ttu-id="5454b-116">Profil oluşturma yapıları</span><span class="sxs-lookup"><span data-stu-id="5454b-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
