---
title: "COR_VERSION Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_VERSION
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_VERSION
helpviewer_keywords: COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bd4a878b51685befb39eb486097be2e2f2c1d409
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="corversion-structure"></a><span data-ttu-id="75aac-102">COR_VERSION Yapısı</span><span class="sxs-lookup"><span data-stu-id="75aac-102">COR_VERSION Structure</span></span>
<span data-ttu-id="75aac-103">Ortak dil çalışma zamanı standart dört bölümden oluşan sürüm numarasını depolar.</span><span class="sxs-lookup"><span data-stu-id="75aac-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75aac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75aac-104">Syntax</span></span>  
  
```  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="75aac-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="75aac-105">Members</span></span>  
  
|<span data-ttu-id="75aac-106">Üye</span><span class="sxs-lookup"><span data-stu-id="75aac-106">Member</span></span>|<span data-ttu-id="75aac-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75aac-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="75aac-108">Ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="75aac-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="75aac-109">İkincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="75aac-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="75aac-110">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="75aac-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="75aac-111">Alt yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="75aac-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75aac-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75aac-112">Remarks</span></span>  
 <span data-ttu-id="75aac-113">Sürüm numarası 1.0.3705.288 ise, ana sürüm numarasını 1., ikincil sürüm numarası 0 olduğundan, 3705 yapı numarasıdır ve 288 alt yapı numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="75aac-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75aac-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75aac-114">Requirements</span></span>  
 <span data-ttu-id="75aac-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75aac-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75aac-116">**Başlık:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="75aac-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="75aac-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75aac-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75aac-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75aac-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75aac-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="75aac-119">See Also</span></span>  
 [<span data-ttu-id="75aac-120">Hata ayıklama yapıları</span><span class="sxs-lookup"><span data-stu-id="75aac-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="75aac-121">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="75aac-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
