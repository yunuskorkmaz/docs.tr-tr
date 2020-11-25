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
ms.openlocfilehash: 81d47a3e4d72f991dc15924e7ff1ecc8df2e7322
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706066"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="4ae2b-102">CorSaveSize Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4ae2b-102">CorSaveSize Enumeration</span></span>

<span data-ttu-id="4ae2b-103">Bir kaydetme işleminin boyutunu sorgularken gereken duyarlık düzeyini gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4ae2b-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ae2b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4ae2b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,
    cssQuick                   = 0x0001,
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="4ae2b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4ae2b-105">Members</span></span>  
  
|<span data-ttu-id="4ae2b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4ae2b-106">Member</span></span>|<span data-ttu-id="4ae2b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ae2b-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="4ae2b-108">Dönüş değerinin tam olarak doğru olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ae2b-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="4ae2b-109">Dönüş değerinin tahmini olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ae2b-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="4ae2b-110">Discardable türlerinin kaldırılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ae2b-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ae2b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ae2b-111">Requirements</span></span>  

 <span data-ttu-id="4ae2b-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ae2b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ae2b-113">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="4ae2b-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4ae2b-114">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4ae2b-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4ae2b-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ae2b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ae2b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ae2b-116">See also</span></span>

- [<span data-ttu-id="4ae2b-117">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="4ae2b-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
