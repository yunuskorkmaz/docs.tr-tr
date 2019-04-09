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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02ff60852a85d003deb68cae96a184ac8d61c65f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089418"
---
# <a name="corpubenumprocess-enumeration"></a><span data-ttu-id="f056d-102">COR_PUB_ENUMPROCESS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f056d-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="f056d-103">Numaralandırılacak işlem türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f056d-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f056d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f056d-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="f056d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f056d-105">Members</span></span>  
  
|<span data-ttu-id="f056d-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="f056d-106">Member name</span></span>|<span data-ttu-id="f056d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f056d-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="f056d-108">Yönetilen bir işlem.</span><span class="sxs-lookup"><span data-stu-id="f056d-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f056d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f056d-109">Remarks</span></span>  
 <span data-ttu-id="f056d-110">Yönetilmeyen hata ayıklama API'ın geçerli sürümü yalnızca işlemler yönetilen numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="f056d-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f056d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f056d-111">Requirements</span></span>  
 <span data-ttu-id="f056d-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f056d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f056d-113">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="f056d-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f056d-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f056d-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f056d-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f056d-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f056d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f056d-116">See also</span></span>

- [<span data-ttu-id="f056d-117">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="f056d-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
