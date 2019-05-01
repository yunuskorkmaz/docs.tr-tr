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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045389"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="4724b-102">CorSaveSize Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4724b-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="4724b-103">Kaydetme boyutu için sorgulanırken gerekli duyarlık düzeyini belirten değerleri içeren işlemi.</span><span class="sxs-lookup"><span data-stu-id="4724b-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4724b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4724b-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="4724b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4724b-105">Members</span></span>  
  
|<span data-ttu-id="4724b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4724b-106">Member</span></span>|<span data-ttu-id="4724b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4724b-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="4724b-108">Dönüş değeri tam olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4724b-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="4724b-109">Dönüş değeri tahmini olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4724b-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="4724b-110">Discardable türleri kaldırılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4724b-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4724b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4724b-111">Requirements</span></span>  
 <span data-ttu-id="4724b-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4724b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4724b-113">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="4724b-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4724b-114">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="4724b-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4724b-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4724b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4724b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4724b-116">See also</span></span>

- [<span data-ttu-id="4724b-117">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="4724b-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
