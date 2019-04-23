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
ms.openlocfilehash: 00e58d83c19c3cb6a2e1eb38942500d7f5dc5cf9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118930"
---
# <a name="corversion-structure"></a><span data-ttu-id="b2c38-102">COR_VERSION Yapısı</span><span class="sxs-lookup"><span data-stu-id="b2c38-102">COR_VERSION Structure</span></span>
<span data-ttu-id="b2c38-103">Ortak dil çalışma zamanı standart Dört bölümlü sürüm numarasını depolar.</span><span class="sxs-lookup"><span data-stu-id="b2c38-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2c38-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2c38-104">Syntax</span></span>  
  
```  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="b2c38-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b2c38-105">Members</span></span>  
  
|<span data-ttu-id="b2c38-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b2c38-106">Member</span></span>|<span data-ttu-id="b2c38-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2c38-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="b2c38-108">Ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="b2c38-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="b2c38-109">İkincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="b2c38-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="b2c38-110">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="b2c38-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="b2c38-111">Alt yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="b2c38-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2c38-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2c38-112">Remarks</span></span>  
 <span data-ttu-id="b2c38-113">Sürüm numarasını 1.0.3705.288 ise, 1. ana sürüm numarası, ikincil sürüm numarası 0 ise, 3705 yapı numarasıdır ve 288 alt yapı numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="b2c38-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2c38-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2c38-114">Requirements</span></span>  
 <span data-ttu-id="b2c38-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2c38-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2c38-116">**Üst bilgi:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="b2c38-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="b2c38-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2c38-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2c38-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2c38-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c38-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2c38-119">See also</span></span>

- [<span data-ttu-id="b2c38-120">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="b2c38-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="b2c38-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b2c38-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
