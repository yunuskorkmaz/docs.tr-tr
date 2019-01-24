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
ms.openlocfilehash: e9ed3cdac726fbdbf9ee2b33f42565d8594bc36e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669685"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="2a54c-102">CorLocalRefPreservation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="2a54c-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="2a54c-103">Yerel başvurular alınmasına yönelik bayrak değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="2a54c-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a54c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a54c-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="2a54c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2a54c-105">Members</span></span>  
  
|<span data-ttu-id="2a54c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2a54c-106">Member</span></span>|<span data-ttu-id="2a54c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a54c-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="2a54c-108">Yerel başvuru korur.</span><span class="sxs-lookup"><span data-stu-id="2a54c-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="2a54c-109">Yerel tür başvurularını korur.</span><span class="sxs-lookup"><span data-stu-id="2a54c-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="2a54c-110">Yerel üye başvuruları korur.</span><span class="sxs-lookup"><span data-stu-id="2a54c-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a54c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a54c-111">Requirements</span></span>  
 <span data-ttu-id="2a54c-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a54c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a54c-113">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="2a54c-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2a54c-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a54c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a54c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a54c-115">See also</span></span>
- [<span data-ttu-id="2a54c-116">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="2a54c-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
