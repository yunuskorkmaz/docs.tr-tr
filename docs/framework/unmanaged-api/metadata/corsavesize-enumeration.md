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
ms.openlocfilehash: c1e7bbac17d9a9ae191a5ad6d69b52a806383562
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781607"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="ea752-102">CorSaveSize Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ea752-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="ea752-103">Kaydetme boyutu için sorgulanırken gerekli duyarlık düzeyini belirten değerleri içeren işlemi.</span><span class="sxs-lookup"><span data-stu-id="ea752-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea752-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea752-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="ea752-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ea752-105">Members</span></span>  
  
|<span data-ttu-id="ea752-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ea752-106">Member</span></span>|<span data-ttu-id="ea752-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea752-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="ea752-108">Dönüş değeri tam olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea752-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="ea752-109">Dönüş değeri tahmini olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea752-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="ea752-110">Discardable türleri kaldırılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea752-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ea752-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea752-111">Requirements</span></span>  
 <span data-ttu-id="ea752-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea752-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea752-113">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="ea752-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ea752-114">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="ea752-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea752-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea752-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea752-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea752-116">See also</span></span>

- [<span data-ttu-id="ea752-117">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ea752-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
