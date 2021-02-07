---
description: 'Daha fazla bilgi edinin: CVStruct yapısı'
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
ms.openlocfilehash: 25e8073f75620bca0737b11499d318cd57d6101c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707221"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="09266-103">CVStruct Yapısı</span><span class="sxs-lookup"><span data-stu-id="09266-103">CVStruct Structure</span></span>

<span data-ttu-id="09266-104">Bir modül veya bileşik görüntü yüklerken kullanılan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="09266-104">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09266-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="09266-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="09266-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="09266-106">Members</span></span>  
  
|<span data-ttu-id="09266-107">Üye</span><span class="sxs-lookup"><span data-stu-id="09266-107">Member</span></span>|<span data-ttu-id="09266-108">Description</span><span class="sxs-lookup"><span data-stu-id="09266-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="09266-109">Ana</span><span class="sxs-lookup"><span data-stu-id="09266-109">Major</span></span>|<span data-ttu-id="09266-110">Ana sürüm yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="09266-110">Major version build number.</span></span>|  
|<span data-ttu-id="09266-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="09266-111">Minor</span></span>|<span data-ttu-id="09266-112">İkincil sürüm yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="09266-112">Minor version build number.</span></span>|  
|<span data-ttu-id="09266-113">Alt</span><span class="sxs-lookup"><span data-stu-id="09266-113">Sub</span></span>|<span data-ttu-id="09266-114">Alt yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="09266-114">Sub-build number.</span></span>|  
|<span data-ttu-id="09266-115">Oluşturma</span><span class="sxs-lookup"><span data-stu-id="09266-115">Build</span></span>|<span data-ttu-id="09266-116">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="09266-116">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09266-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09266-117">Requirements</span></span>  

 <span data-ttu-id="09266-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09266-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09266-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="09266-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09266-120">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="09266-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="09266-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09266-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09266-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09266-122">See also</span></span>

- [<span data-ttu-id="09266-123">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="09266-123">Metadata Structures</span></span>](metadata-structures.md)
