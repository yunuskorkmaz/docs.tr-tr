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
ms.openlocfilehash: 49b0298f4fa776c93f89ac380ce65568b493379b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677121"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="52334-102">CorLocalRefPreservation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="52334-102">CorLocalRefPreservation Enumeration</span></span>

<span data-ttu-id="52334-103">Yerel başvuruların işleme için bayrak değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="52334-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52334-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="52334-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="52334-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="52334-105">Members</span></span>  
  
|<span data-ttu-id="52334-106">Üye</span><span class="sxs-lookup"><span data-stu-id="52334-106">Member</span></span>|<span data-ttu-id="52334-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52334-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="52334-108">Yerel başvuruları koru.</span><span class="sxs-lookup"><span data-stu-id="52334-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="52334-109">Yerel tür başvurularını koru.</span><span class="sxs-lookup"><span data-stu-id="52334-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="52334-110">Yerel üye başvurularını koruma.</span><span class="sxs-lookup"><span data-stu-id="52334-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52334-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52334-111">Requirements</span></span>  

 <span data-ttu-id="52334-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52334-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52334-113">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="52334-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="52334-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52334-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52334-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52334-115">See also</span></span>

- [<span data-ttu-id="52334-116">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="52334-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
