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
ms.openlocfilehash: bc36468a2016822e884ec3a36a23c75477a00a2d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217204"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="6d2c9-102">CorSaveSize Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6d2c9-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="6d2c9-103">Kaydetme boyutu için sorgulanırken gerekli duyarlık düzeyini belirten değerleri içeren işlemi.</span><span class="sxs-lookup"><span data-stu-id="6d2c9-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d2c9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d2c9-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="6d2c9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6d2c9-105">Members</span></span>  
  
|<span data-ttu-id="6d2c9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6d2c9-106">Member</span></span>|<span data-ttu-id="6d2c9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d2c9-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="6d2c9-108">Dönüş değeri tam olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6d2c9-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="6d2c9-109">Dönüş değeri tahmini olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6d2c9-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="6d2c9-110">Discardable türleri kaldırılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6d2c9-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6d2c9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d2c9-111">Requirements</span></span>  
 <span data-ttu-id="6d2c9-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d2c9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d2c9-113">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="6d2c9-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="6d2c9-114">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="6d2c9-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="6d2c9-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="6d2c9-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6d2c9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d2c9-116">See also</span></span>

- [<span data-ttu-id="6d2c9-117">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="6d2c9-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
