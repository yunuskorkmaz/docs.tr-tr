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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66f9f95b0cf19acb677daf7f7401d21cc81864a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447613"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="58d76-102">CorSaveSize Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="58d76-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="58d76-103">Kaydetme boyutu için sorgulanırken gerekli duyarlık düzeyini gösteren değerleri içeren işlemi.</span><span class="sxs-lookup"><span data-stu-id="58d76-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58d76-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58d76-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="58d76-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="58d76-105">Members</span></span>  
  
|<span data-ttu-id="58d76-106">Üye</span><span class="sxs-lookup"><span data-stu-id="58d76-106">Member</span></span>|<span data-ttu-id="58d76-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58d76-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="58d76-108">Dönüş değeri tam olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="58d76-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="58d76-109">Dönüş değeri tahmini olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="58d76-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="58d76-110">Discardable türleri kaldırılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="58d76-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="58d76-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58d76-111">Requirements</span></span>  
 <span data-ttu-id="58d76-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58d76-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58d76-113">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="58d76-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="58d76-114">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="58d76-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="58d76-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58d76-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58d76-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58d76-116">See Also</span></span>  
 [<span data-ttu-id="58d76-117">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="58d76-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
