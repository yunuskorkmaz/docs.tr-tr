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
ms.openlocfilehash: 19ee3097dfe80ba9dcbdaf316db0fd165b50abc6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436419"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="a67a8-102">CVStruct Yapısı</span><span class="sxs-lookup"><span data-stu-id="a67a8-102">CVStruct Structure</span></span>
<span data-ttu-id="a67a8-103">Bir modül veya bileşik görüntü yüklerken kullanılan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a67a8-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a67a8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a67a8-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="a67a8-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="a67a8-105">Members</span></span>  
  
|<span data-ttu-id="a67a8-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="a67a8-106">Member</span></span>|<span data-ttu-id="a67a8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a67a8-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a67a8-108">düzeltme sınıfı,</span><span class="sxs-lookup"><span data-stu-id="a67a8-108">Major</span></span>|<span data-ttu-id="a67a8-109">Ana sürüm yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="a67a8-109">Major version build number.</span></span>|  
|<span data-ttu-id="a67a8-110">düzeltme sınıfı,</span><span class="sxs-lookup"><span data-stu-id="a67a8-110">Minor</span></span>|<span data-ttu-id="a67a8-111">İkincil sürüm yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="a67a8-111">Minor version build number.</span></span>|  
|<span data-ttu-id="a67a8-112">Alt</span><span class="sxs-lookup"><span data-stu-id="a67a8-112">Sub</span></span>|<span data-ttu-id="a67a8-113">Alt yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="a67a8-113">Sub-build number.</span></span>|  
|<span data-ttu-id="a67a8-114">{1&gt;Yapı (Build)&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a67a8-114">Build</span></span>|<span data-ttu-id="a67a8-115">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="a67a8-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a67a8-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a67a8-116">Requirements</span></span>  
 <span data-ttu-id="a67a8-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a67a8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a67a8-118">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a67a8-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a67a8-119">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a67a8-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a67a8-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a67a8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a67a8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a67a8-121">See also</span></span>

- [<span data-ttu-id="a67a8-122">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="a67a8-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
