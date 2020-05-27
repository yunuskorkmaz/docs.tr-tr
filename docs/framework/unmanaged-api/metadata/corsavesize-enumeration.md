---
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
ms.openlocfilehash: 22a7f87a5803dc185052a5ce7ed427eff9f8fb18
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009190"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="be750-102">CorSaveSize Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="be750-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="be750-103">Bir kaydetme işleminin boyutunu sorgularken gereken duyarlık düzeyini gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="be750-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be750-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be750-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,
    cssQuick                   = 0x0001,
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="be750-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="be750-105">Members</span></span>  
  
|<span data-ttu-id="be750-106">Üye</span><span class="sxs-lookup"><span data-stu-id="be750-106">Member</span></span>|<span data-ttu-id="be750-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be750-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="be750-108">Dönüş değerinin tam olarak doğru olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="be750-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="be750-109">Dönüş değerinin tahmini olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="be750-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="be750-110">Discardable türlerinin kaldırılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="be750-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be750-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be750-111">Requirements</span></span>  
 <span data-ttu-id="be750-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be750-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be750-113">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="be750-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="be750-114">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="be750-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be750-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be750-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be750-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be750-116">See also</span></span>

- [<span data-ttu-id="be750-117">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="be750-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
