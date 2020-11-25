---
title: COR_PUB_ENUMPROCESS Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PUB_ENUMPROCESS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_PUB_ENUMPROCESS
helpviewer_keywords:
- COR_PUB_ENUMPROCESS enumeration [.NET Framework debugging]
ms.assetid: 5d3ada6e-feea-47da-a7ed-b664107c137f
topic_type:
- apiref
ms.openlocfilehash: 30a522fbf96aebaa96f33f4a1dc381683f183871
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726424"
---
# <a name="cor_pub_enumprocess-enumeration"></a><span data-ttu-id="f2eeb-102">COR_PUB_ENUMPROCESS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f2eeb-102">COR_PUB_ENUMPROCESS Enumeration</span></span>

<span data-ttu-id="f2eeb-103">Numaralandırılacak işlemin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2eeb-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2eeb-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f2eeb-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="f2eeb-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f2eeb-105">Members</span></span>  
  
|<span data-ttu-id="f2eeb-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="f2eeb-106">Member name</span></span>|<span data-ttu-id="f2eeb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2eeb-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="f2eeb-108">Yönetilen bir işlem.</span><span class="sxs-lookup"><span data-stu-id="f2eeb-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2eeb-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2eeb-109">Remarks</span></span>  

 <span data-ttu-id="f2eeb-110">Yönetilmeyen hata ayıklama API 'sinin geçerli sürümü yalnızca yönetilen işlemi numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="f2eeb-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2eeb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2eeb-111">Requirements</span></span>  

 <span data-ttu-id="f2eeb-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2eeb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2eeb-113">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="f2eeb-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f2eeb-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f2eeb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2eeb-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2eeb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2eeb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2eeb-116">See also</span></span>

- [<span data-ttu-id="f2eeb-117">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="f2eeb-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
