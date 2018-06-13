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
ms.openlocfilehash: ee808ba403a513b897134420b45ebe8cd3537571
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442252"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="f1db8-102">CorLocalRefPreservation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f1db8-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="f1db8-103">Yerel başvuruları işlenmesi için bayrak değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="f1db8-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1db8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1db8-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="f1db8-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f1db8-105">Members</span></span>  
  
|<span data-ttu-id="f1db8-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f1db8-106">Member</span></span>|<span data-ttu-id="f1db8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1db8-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="f1db8-108">Yerel başvuru korur.</span><span class="sxs-lookup"><span data-stu-id="f1db8-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="f1db8-109">Yerel tür başvuruları korur.</span><span class="sxs-lookup"><span data-stu-id="f1db8-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="f1db8-110">Yerel üye başvuruları korur.</span><span class="sxs-lookup"><span data-stu-id="f1db8-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1db8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1db8-111">Requirements</span></span>  
 <span data-ttu-id="f1db8-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1db8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1db8-113">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f1db8-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f1db8-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1db8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1db8-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1db8-115">See Also</span></span>  
 [<span data-ttu-id="f1db8-116">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f1db8-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
