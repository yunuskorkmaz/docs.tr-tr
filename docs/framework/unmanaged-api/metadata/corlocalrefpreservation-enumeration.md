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
ms.openlocfilehash: 42cb4e76bb77aebcee3b28035635a877513cdc04
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008995"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="25055-102">CorLocalRefPreservation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="25055-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="25055-103">Yerel başvuruların işleme için bayrak değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="25055-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25055-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25055-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="25055-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="25055-105">Members</span></span>  
  
|<span data-ttu-id="25055-106">Üye</span><span class="sxs-lookup"><span data-stu-id="25055-106">Member</span></span>|<span data-ttu-id="25055-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25055-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="25055-108">Yerel başvuruları koru.</span><span class="sxs-lookup"><span data-stu-id="25055-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="25055-109">Yerel tür başvurularını koru.</span><span class="sxs-lookup"><span data-stu-id="25055-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="25055-110">Yerel üye başvurularını koruma.</span><span class="sxs-lookup"><span data-stu-id="25055-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25055-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25055-111">Requirements</span></span>  
 <span data-ttu-id="25055-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25055-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25055-113">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="25055-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="25055-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25055-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25055-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25055-115">See also</span></span>

- [<span data-ttu-id="25055-116">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="25055-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
