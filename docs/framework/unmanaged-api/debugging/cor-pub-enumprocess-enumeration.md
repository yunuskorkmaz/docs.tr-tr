---
description: 'Hakkında daha fazla bilgi edinin: COR_PUB_ENUMPROCESS numaralandırması'
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
ms.openlocfilehash: 66bbd08aabb9d2c93e385ed098bae54754a85b85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801793"
---
# <a name="cor_pub_enumprocess-enumeration"></a><span data-ttu-id="acf7d-103">COR_PUB_ENUMPROCESS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="acf7d-103">COR_PUB_ENUMPROCESS Enumeration</span></span>

<span data-ttu-id="acf7d-104">Numaralandırılacak işlemin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="acf7d-104">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acf7d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="acf7d-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="acf7d-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="acf7d-106">Members</span></span>  
  
|<span data-ttu-id="acf7d-107">Üye adı</span><span class="sxs-lookup"><span data-stu-id="acf7d-107">Member name</span></span>|<span data-ttu-id="acf7d-108">Description</span><span class="sxs-lookup"><span data-stu-id="acf7d-108">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="acf7d-109">Yönetilen bir işlem.</span><span class="sxs-lookup"><span data-stu-id="acf7d-109">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acf7d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="acf7d-110">Remarks</span></span>  

 <span data-ttu-id="acf7d-111">Yönetilmeyen hata ayıklama API 'sinin geçerli sürümü yalnızca yönetilen işlemi numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="acf7d-111">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acf7d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="acf7d-112">Requirements</span></span>  

 <span data-ttu-id="acf7d-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acf7d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acf7d-114">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="acf7d-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="acf7d-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="acf7d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acf7d-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acf7d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acf7d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acf7d-117">See also</span></span>

- [<span data-ttu-id="acf7d-118">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="acf7d-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
