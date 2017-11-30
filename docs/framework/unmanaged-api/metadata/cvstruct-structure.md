---
title: "CVStruct Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CVStruct
api_location: mscoree.dll
api_type: COM
f1_keywords: CVStruct
helpviewer_keywords: CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 95c1aeb0cacef929e99e5121f29e2f69b320caec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cvstruct-structure"></a><span data-ttu-id="b95db-102">CVStruct Yapısı</span><span class="sxs-lookup"><span data-stu-id="b95db-102">CVStruct Structure</span></span>
<span data-ttu-id="b95db-103">Bir modül veya bileşik görüntü yüklenirken kullanılan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="b95db-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b95db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b95db-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="b95db-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b95db-105">Members</span></span>  
  
|<span data-ttu-id="b95db-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b95db-106">Member</span></span>|<span data-ttu-id="b95db-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b95db-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b95db-108">Ana</span><span class="sxs-lookup"><span data-stu-id="b95db-108">Major</span></span>|<span data-ttu-id="b95db-109">Ana sürüm yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="b95db-109">Major version build number.</span></span>|  
|<span data-ttu-id="b95db-110">Küçük</span><span class="sxs-lookup"><span data-stu-id="b95db-110">Minor</span></span>|<span data-ttu-id="b95db-111">İkincil sürüm yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="b95db-111">Minor version build number.</span></span>|  
|<span data-ttu-id="b95db-112">Alt</span><span class="sxs-lookup"><span data-stu-id="b95db-112">Sub</span></span>|<span data-ttu-id="b95db-113">Alt yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="b95db-113">Sub-build number.</span></span>|  
|<span data-ttu-id="b95db-114">Derleme</span><span class="sxs-lookup"><span data-stu-id="b95db-114">Build</span></span>|<span data-ttu-id="b95db-115">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="b95db-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b95db-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b95db-116">Requirements</span></span>  
 <span data-ttu-id="b95db-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b95db-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b95db-118">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b95db-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b95db-119">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b95db-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b95db-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b95db-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b95db-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b95db-121">See Also</span></span>  
 [<span data-ttu-id="b95db-122">Meta veri yapıları</span><span class="sxs-lookup"><span data-stu-id="b95db-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
