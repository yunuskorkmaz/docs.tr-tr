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
ms.openlocfilehash: e2668e36debebb5ba71277912f37833eba584fde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403285"
---
# <a name="corversion-structure"></a><span data-ttu-id="3528f-102">COR_VERSION Yapısı</span><span class="sxs-lookup"><span data-stu-id="3528f-102">COR_VERSION Structure</span></span>
<span data-ttu-id="3528f-103">Ortak dil çalışma zamanı standart dört bölümden oluşan sürüm numarasını depolar.</span><span class="sxs-lookup"><span data-stu-id="3528f-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3528f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3528f-104">Syntax</span></span>  
  
```  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="3528f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3528f-105">Members</span></span>  
  
|<span data-ttu-id="3528f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3528f-106">Member</span></span>|<span data-ttu-id="3528f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3528f-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="3528f-108">Ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="3528f-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="3528f-109">İkincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="3528f-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="3528f-110">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="3528f-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="3528f-111">Alt yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="3528f-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3528f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3528f-112">Remarks</span></span>  
 <span data-ttu-id="3528f-113">Sürüm numarası 1.0.3705.288 ise, ana sürüm numarasını 1., ikincil sürüm numarası 0 olduğundan, 3705 yapı numarasıdır ve 288 alt yapı numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="3528f-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3528f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3528f-114">Requirements</span></span>  
 <span data-ttu-id="3528f-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3528f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3528f-116">**Başlık:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="3528f-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="3528f-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3528f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3528f-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3528f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3528f-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3528f-119">See Also</span></span>  
 [<span data-ttu-id="3528f-120">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="3528f-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="3528f-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="3528f-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
