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
ms.openlocfilehash: b1f0a36d186c6d9788d43b075bf9d67c36ed1acb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740559"
---
# <a name="corversion-structure"></a><span data-ttu-id="45cea-102">COR_VERSION Yapısı</span><span class="sxs-lookup"><span data-stu-id="45cea-102">COR_VERSION Structure</span></span>
<span data-ttu-id="45cea-103">Ortak dil çalışma zamanı standart Dört bölümlü sürüm numarasını depolar.</span><span class="sxs-lookup"><span data-stu-id="45cea-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45cea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45cea-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="45cea-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="45cea-105">Members</span></span>  
  
|<span data-ttu-id="45cea-106">Üye</span><span class="sxs-lookup"><span data-stu-id="45cea-106">Member</span></span>|<span data-ttu-id="45cea-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45cea-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="45cea-108">Ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="45cea-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="45cea-109">İkincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="45cea-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="45cea-110">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="45cea-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="45cea-111">Alt yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="45cea-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45cea-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45cea-112">Remarks</span></span>  
 <span data-ttu-id="45cea-113">Sürüm numarasını 1.0.3705.288 ise, 1. ana sürüm numarası, ikincil sürüm numarası 0 ise, 3705 yapı numarasıdır ve 288 alt yapı numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="45cea-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45cea-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45cea-114">Requirements</span></span>  
 <span data-ttu-id="45cea-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45cea-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45cea-116">**Üst bilgi:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="45cea-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="45cea-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45cea-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45cea-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45cea-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45cea-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45cea-119">See also</span></span>

- [<span data-ttu-id="45cea-120">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="45cea-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="45cea-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="45cea-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
