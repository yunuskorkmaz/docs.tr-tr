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
ms.openlocfilehash: b3e35cea4601c8e51eb3021dc9f598ddb881afe0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750715"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="7103a-102">CVStruct Yapısı</span><span class="sxs-lookup"><span data-stu-id="7103a-102">CVStruct Structure</span></span>
<span data-ttu-id="7103a-103">Bir modül veya bileşik görüntü yüklerken kullanılan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="7103a-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7103a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7103a-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="7103a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7103a-105">Members</span></span>  
  
|<span data-ttu-id="7103a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7103a-106">Member</span></span>|<span data-ttu-id="7103a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7103a-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7103a-108">Ana</span><span class="sxs-lookup"><span data-stu-id="7103a-108">Major</span></span>|<span data-ttu-id="7103a-109">Ana sürüm yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="7103a-109">Major version build number.</span></span>|  
|<span data-ttu-id="7103a-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="7103a-110">Minor</span></span>|<span data-ttu-id="7103a-111">İkincil sürüm derleme numarası.</span><span class="sxs-lookup"><span data-stu-id="7103a-111">Minor version build number.</span></span>|  
|<span data-ttu-id="7103a-112">Alt</span><span class="sxs-lookup"><span data-stu-id="7103a-112">Sub</span></span>|<span data-ttu-id="7103a-113">Alt yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="7103a-113">Sub-build number.</span></span>|  
|<span data-ttu-id="7103a-114">Yapı</span><span class="sxs-lookup"><span data-stu-id="7103a-114">Build</span></span>|<span data-ttu-id="7103a-115">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="7103a-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7103a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7103a-116">Requirements</span></span>  
 <span data-ttu-id="7103a-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7103a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7103a-118">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7103a-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7103a-119">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="7103a-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7103a-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7103a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7103a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7103a-121">See also</span></span>

- [<span data-ttu-id="7103a-122">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="7103a-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
