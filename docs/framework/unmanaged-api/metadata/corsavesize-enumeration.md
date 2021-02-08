---
description: 'Daha fazla bilgi edinin: CorSaveSize numaralandırması'
title: CorSaveSize Numaralandırması
ms.date: 03/30/2017
api_name:
- CorSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSaveSize
helpviewer_keywords:
- CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type:
- apiref
ms.openlocfilehash: 47e2d4d77f58f8f1c2135da5867dfa47cedfd83d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784229"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="c9f24-103">CorSaveSize Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9f24-103">CorSaveSize Enumeration</span></span>

<span data-ttu-id="c9f24-104">Bir kaydetme işleminin boyutunu sorgularken gereken duyarlık düzeyini gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c9f24-104">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f24-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c9f24-105">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,
    cssQuick                   = 0x0001,
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="c9f24-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c9f24-106">Members</span></span>  
  
|<span data-ttu-id="c9f24-107">Üye</span><span class="sxs-lookup"><span data-stu-id="c9f24-107">Member</span></span>|<span data-ttu-id="c9f24-108">Description</span><span class="sxs-lookup"><span data-stu-id="c9f24-108">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="c9f24-109">Dönüş değerinin tam olarak doğru olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9f24-109">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="c9f24-110">Dönüş değerinin tahmini olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9f24-110">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="c9f24-111">Discardable türlerinin kaldırılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9f24-111">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9f24-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9f24-112">Requirements</span></span>  

 <span data-ttu-id="c9f24-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9f24-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9f24-114">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="c9f24-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c9f24-115">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c9f24-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9f24-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9f24-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f24-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9f24-117">See also</span></span>

- [<span data-ttu-id="c9f24-118">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="c9f24-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
