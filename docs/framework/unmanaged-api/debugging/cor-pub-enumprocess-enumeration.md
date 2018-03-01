---
title: "COR_PUB_ENUMPROCESS Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d92c484c8cb0142f59c26270674af73da5fbfa95
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corpubenumprocess-enumeration"></a><span data-ttu-id="5d9bd-102">COR_PUB_ENUMPROCESS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5d9bd-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="5d9bd-103">Numaralandırılacak işlem türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5d9bd-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d9bd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d9bd-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="5d9bd-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5d9bd-105">Members</span></span>  
  
|<span data-ttu-id="5d9bd-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="5d9bd-106">Member name</span></span>|<span data-ttu-id="5d9bd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d9bd-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="5d9bd-108">Yönetilen bir işlem.</span><span class="sxs-lookup"><span data-stu-id="5d9bd-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d9bd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d9bd-109">Remarks</span></span>  
 <span data-ttu-id="5d9bd-110">Yönetilmeyen hata ayıklama API'si geçerli sürümü yalnızca işlemleri yönetilen numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="5d9bd-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d9bd-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d9bd-111">Requirements</span></span>  
 <span data-ttu-id="5d9bd-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d9bd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d9bd-113">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="5d9bd-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="5d9bd-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d9bd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d9bd-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d9bd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d9bd-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d9bd-116">See Also</span></span>  
 [<span data-ttu-id="5d9bd-117">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="5d9bd-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
