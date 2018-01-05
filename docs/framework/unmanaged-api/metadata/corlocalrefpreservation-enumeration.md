---
title: CorLocalRefPreservation Sabit Listesi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorLocalRefPreservation
api_location: mscoree.dll
api_type: COM
f1_keywords: CorLocalRefPreservation
helpviewer_keywords: CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c35bbfef62f65a9a401d00f9ae56e2f4c00bb0b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="e2f9a-102">CorLocalRefPreservation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e2f9a-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="e2f9a-103">Yerel başvuruları işlenmesi için bayrak değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="e2f9a-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2f9a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2f9a-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="e2f9a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e2f9a-105">Members</span></span>  
  
|<span data-ttu-id="e2f9a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e2f9a-106">Member</span></span>|<span data-ttu-id="e2f9a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2f9a-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="e2f9a-108">Yerel başvuru korur.</span><span class="sxs-lookup"><span data-stu-id="e2f9a-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="e2f9a-109">Yerel tür başvuruları korur.</span><span class="sxs-lookup"><span data-stu-id="e2f9a-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="e2f9a-110">Yerel üye başvuruları korur.</span><span class="sxs-lookup"><span data-stu-id="e2f9a-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2f9a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2f9a-111">Requirements</span></span>  
 <span data-ttu-id="e2f9a-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2f9a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2f9a-113">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e2f9a-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e2f9a-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2f9a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f9a-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2f9a-115">See Also</span></span>  
 [<span data-ttu-id="e2f9a-116">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e2f9a-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
