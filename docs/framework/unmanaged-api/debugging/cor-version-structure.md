---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffbe571ebc3d14c12e57b1f805d77e56e97d12e1
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274182"
---
# <a name="cor_version-structure"></a><span data-ttu-id="d668c-102">COR_VERSION Yapısı</span><span class="sxs-lookup"><span data-stu-id="d668c-102">COR_VERSION Structure</span></span>
<span data-ttu-id="d668c-103">Ortak dil çalışma zamanının Standart Dört parçalı sürüm numarasını depolar.</span><span class="sxs-lookup"><span data-stu-id="d668c-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d668c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d668c-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="d668c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d668c-105">Members</span></span>  
  
|<span data-ttu-id="d668c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d668c-106">Member</span></span>|<span data-ttu-id="d668c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d668c-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="d668c-108">Ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="d668c-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="d668c-109">İkincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="d668c-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="d668c-110">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="d668c-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="d668c-111">Alt yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="d668c-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d668c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d668c-112">Remarks</span></span>  
 <span data-ttu-id="d668c-113">Sürüm numarası 1.0.3705.288 ise, 1 ana sürüm numarasıdır, 0 küçük sürüm numarasıdır, 3705 derleme numarasıdır ve 288 alt yapı numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="d668c-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d668c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d668c-114">Requirements</span></span>  
 <span data-ttu-id="d668c-115">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d668c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d668c-116">**Üst bilgi** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="d668c-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="d668c-117">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d668c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d668c-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d668c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d668c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d668c-119">See also</span></span>

- [<span data-ttu-id="d668c-120">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="d668c-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="d668c-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d668c-121">Debugging</span></span>](index.md)
