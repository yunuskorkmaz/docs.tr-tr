---
description: 'Daha fazla bilgi edinin: COR_VERSION yapısı'
title: COR_VERSION Yapısı
ms.date: 03/30/2017
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
ms.openlocfilehash: abdbe2a62d89db9dd673a429d81209fc42c34b73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801780"
---
# <a name="cor_version-structure"></a><span data-ttu-id="e9655-103">COR_VERSION Yapısı</span><span class="sxs-lookup"><span data-stu-id="e9655-103">COR_VERSION Structure</span></span>

<span data-ttu-id="e9655-104">Ortak dil çalışma zamanının Standart Dört parçalı sürüm numarasını depolar.</span><span class="sxs-lookup"><span data-stu-id="e9655-104">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9655-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e9655-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="e9655-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e9655-106">Members</span></span>  
  
|<span data-ttu-id="e9655-107">Üye</span><span class="sxs-lookup"><span data-stu-id="e9655-107">Member</span></span>|<span data-ttu-id="e9655-108">Description</span><span class="sxs-lookup"><span data-stu-id="e9655-108">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="e9655-109">Ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="e9655-109">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="e9655-110">İkincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="e9655-110">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="e9655-111">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="e9655-111">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="e9655-112">Alt yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="e9655-112">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9655-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9655-113">Remarks</span></span>  

 <span data-ttu-id="e9655-114">Sürüm numarası 1.0.3705.288 ise, 1 ana sürüm numarasıdır, 0 küçük sürüm numarasıdır, 3705 derleme numarasıdır ve 288 alt yapı numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="e9655-114">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9655-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9655-115">Requirements</span></span>  

 <span data-ttu-id="e9655-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9655-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9655-117">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="e9655-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="e9655-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e9655-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9655-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9655-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9655-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9655-120">See also</span></span>

- [<span data-ttu-id="e9655-121">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="e9655-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="e9655-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e9655-122">Debugging</span></span>](index.md)
