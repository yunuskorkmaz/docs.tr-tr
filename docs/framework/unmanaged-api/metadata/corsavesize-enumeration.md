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
ms.openlocfilehash: 0f870d9d7d1bc292b213d690df508a6c28bac2ab
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450105"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="73eeb-102">CorSaveSize Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="73eeb-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="73eeb-103">Bir kaydetme işleminin boyutunu sorgularken gereken duyarlık düzeyini gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="73eeb-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73eeb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73eeb-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="73eeb-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="73eeb-105">Members</span></span>  
  
|<span data-ttu-id="73eeb-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="73eeb-106">Member</span></span>|<span data-ttu-id="73eeb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73eeb-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="73eeb-108">Dönüş değerinin tam olarak doğru olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="73eeb-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="73eeb-109">Dönüş değerinin tahmini olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="73eeb-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="73eeb-110">Discardable türlerinin kaldırılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="73eeb-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73eeb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73eeb-111">Requirements</span></span>  
 <span data-ttu-id="73eeb-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73eeb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73eeb-113">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="73eeb-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="73eeb-114">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="73eeb-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="73eeb-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73eeb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73eeb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73eeb-116">See also</span></span>

- [<span data-ttu-id="73eeb-117">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="73eeb-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
