---
title: CorLocalRefPreservation Sabit Listesi
ms.date: 03/30/2017
api_name:
- CorLocalRefPreservation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLocalRefPreservation
helpviewer_keywords:
- CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 845994b96445d8ec2a0e37affc5164b432894a91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102199"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="bb38a-102">CorLocalRefPreservation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="bb38a-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="bb38a-103">Yerel başvurular alınmasına yönelik bayrak değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="bb38a-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb38a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb38a-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="bb38a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bb38a-105">Members</span></span>  
  
|<span data-ttu-id="bb38a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="bb38a-106">Member</span></span>|<span data-ttu-id="bb38a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb38a-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="bb38a-108">Yerel başvuru korur.</span><span class="sxs-lookup"><span data-stu-id="bb38a-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="bb38a-109">Yerel tür başvurularını korur.</span><span class="sxs-lookup"><span data-stu-id="bb38a-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="bb38a-110">Yerel üye başvuruları korur.</span><span class="sxs-lookup"><span data-stu-id="bb38a-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb38a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb38a-111">Requirements</span></span>  
 <span data-ttu-id="bb38a-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb38a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb38a-113">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="bb38a-113">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="bb38a-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="bb38a-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bb38a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb38a-115">See also</span></span>

- [<span data-ttu-id="bb38a-116">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="bb38a-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
