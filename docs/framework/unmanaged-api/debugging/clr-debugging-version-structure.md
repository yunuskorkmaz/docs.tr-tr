---
title: "CLR_DEBUGGING_VERSION Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLR_DEBUGGING_VERSION
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLR_DEBUGGING_VERSION
helpviewer_keywords: CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 98124b7b9efb2c92ebee6b6e99f73edc6cf173a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="clrdebuggingversion-structure"></a><span data-ttu-id="d0418-102">CLR_DEBUGGING_VERSION Yapısı</span><span class="sxs-lookup"><span data-stu-id="d0418-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="d0418-103">Hata ayıklama amacıyla ortak dil çalışma zamanı (CLR) ürün sürümü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d0418-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0418-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0418-104">Syntax</span></span>  
  
```  
Typedef struct _CLR_DEBUGGING_VERSION  
{  
WORD wStructVersion;  
WORD wMajor;   
WORD wMinor;  
WORD wBuild;  
WORD wRevision;  
}  CLR_DEBUGGING_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="d0418-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d0418-105">Members</span></span>  
  
|<span data-ttu-id="d0418-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d0418-106">Member</span></span>|<span data-ttu-id="d0418-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0418-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="d0418-108">Yapı sürüm numarası</span><span class="sxs-lookup"><span data-stu-id="d0418-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="d0418-109">Ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="d0418-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="d0418-110">İkincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="d0418-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="d0418-111">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="d0418-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="d0418-112">Düzeltme numarası.</span><span class="sxs-lookup"><span data-stu-id="d0418-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0418-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0418-113">Remarks</span></span>  
 <span data-ttu-id="d0418-114">`CLR_DEBUGGING_VERSION` Yapısı aynıdır cor_versıon yapısı ancak, `CLR_DEBUGGING_VERSION` yapısı bir ek yapı sürümü alanı sağlar (`wStructVersion`).</span><span class="sxs-lookup"><span data-stu-id="d0418-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="d0418-115">Şu anda, bu alan sıfır olarak ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0418-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0418-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0418-116">Requirements</span></span>  
 <span data-ttu-id="d0418-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0418-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0418-118">**Başlık:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="d0418-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="d0418-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0418-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0418-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0418-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0418-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0418-121">See Also</span></span>  
 [<span data-ttu-id="d0418-122">Hata ayıklama yapıları</span><span class="sxs-lookup"><span data-stu-id="d0418-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="d0418-123">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d0418-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
