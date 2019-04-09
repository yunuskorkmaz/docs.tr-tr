---
title: CVStruct Yapısı
ms.date: 03/30/2017
api_name:
- CVStruct
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CVStruct
helpviewer_keywords:
- CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a5f06b3f79fed5dac5a6f07650e4fabd0aa5867
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142174"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="2680f-102">CVStruct Yapısı</span><span class="sxs-lookup"><span data-stu-id="2680f-102">CVStruct Structure</span></span>
<span data-ttu-id="2680f-103">Bir modül veya bileşik görüntü yüklerken kullanılan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="2680f-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2680f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2680f-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="2680f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2680f-105">Members</span></span>  
  
|<span data-ttu-id="2680f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2680f-106">Member</span></span>|<span data-ttu-id="2680f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2680f-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2680f-108">Ana</span><span class="sxs-lookup"><span data-stu-id="2680f-108">Major</span></span>|<span data-ttu-id="2680f-109">Ana sürüm yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="2680f-109">Major version build number.</span></span>|  
|<span data-ttu-id="2680f-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="2680f-110">Minor</span></span>|<span data-ttu-id="2680f-111">İkincil sürüm derleme numarası.</span><span class="sxs-lookup"><span data-stu-id="2680f-111">Minor version build number.</span></span>|  
|<span data-ttu-id="2680f-112">Alt</span><span class="sxs-lookup"><span data-stu-id="2680f-112">Sub</span></span>|<span data-ttu-id="2680f-113">Alt yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="2680f-113">Sub-build number.</span></span>|  
|<span data-ttu-id="2680f-114">Yapı</span><span class="sxs-lookup"><span data-stu-id="2680f-114">Build</span></span>|<span data-ttu-id="2680f-115">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="2680f-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2680f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2680f-116">Requirements</span></span>  
 <span data-ttu-id="2680f-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2680f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2680f-118">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="2680f-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2680f-119">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="2680f-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="2680f-120">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="2680f-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2680f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2680f-121">See also</span></span>

- [<span data-ttu-id="2680f-122">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="2680f-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
