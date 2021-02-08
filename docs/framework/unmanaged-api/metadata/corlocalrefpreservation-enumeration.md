---
description: 'Daha fazla bilgi edinin: Corlocalrefkoruma numaralandırması'
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
ms.openlocfilehash: afcdf6ce22c5f786e8f728cc1e45ad3ca44e7ef5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784424"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="dca5b-103">CorLocalRefPreservation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="dca5b-103">CorLocalRefPreservation Enumeration</span></span>

<span data-ttu-id="dca5b-104">Yerel başvuruların işleme için bayrak değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="dca5b-104">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dca5b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dca5b-105">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="dca5b-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="dca5b-106">Members</span></span>  
  
|<span data-ttu-id="dca5b-107">Üye</span><span class="sxs-lookup"><span data-stu-id="dca5b-107">Member</span></span>|<span data-ttu-id="dca5b-108">Description</span><span class="sxs-lookup"><span data-stu-id="dca5b-108">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="dca5b-109">Yerel başvuruları koru.</span><span class="sxs-lookup"><span data-stu-id="dca5b-109">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="dca5b-110">Yerel tür başvurularını koru.</span><span class="sxs-lookup"><span data-stu-id="dca5b-110">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="dca5b-111">Yerel üye başvurularını koruma.</span><span class="sxs-lookup"><span data-stu-id="dca5b-111">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dca5b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dca5b-112">Requirements</span></span>  

 <span data-ttu-id="dca5b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dca5b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dca5b-114">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="dca5b-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="dca5b-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dca5b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca5b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dca5b-116">See also</span></span>

- [<span data-ttu-id="dca5b-117">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="dca5b-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
