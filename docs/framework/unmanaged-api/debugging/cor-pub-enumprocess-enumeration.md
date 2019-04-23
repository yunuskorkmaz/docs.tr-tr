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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089418"
---
# <a name="corpubenumprocess-enumeration"></a><span data-ttu-id="d9be0-102">COR_PUB_ENUMPROCESS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d9be0-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="d9be0-103">Numaralandırılacak işlem türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9be0-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9be0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9be0-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="d9be0-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d9be0-105">Members</span></span>  
  
|<span data-ttu-id="d9be0-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="d9be0-106">Member name</span></span>|<span data-ttu-id="d9be0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9be0-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="d9be0-108">Yönetilen bir işlem.</span><span class="sxs-lookup"><span data-stu-id="d9be0-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9be0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9be0-109">Remarks</span></span>  
 <span data-ttu-id="d9be0-110">Yönetilmeyen hata ayıklama API'ın geçerli sürümü yalnızca işlemler yönetilen numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="d9be0-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9be0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9be0-111">Requirements</span></span>  
 <span data-ttu-id="d9be0-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9be0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9be0-113">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="d9be0-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d9be0-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9be0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9be0-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9be0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9be0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9be0-116">See also</span></span>

- [<span data-ttu-id="d9be0-117">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d9be0-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
