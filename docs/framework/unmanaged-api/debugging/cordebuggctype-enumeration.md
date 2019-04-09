---
title: CorDebugGCType Sabit Listesi
ms.date: 03/30/2017
api_name:
- CorDebugGCType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGCType
helpviewer_keywords:
- CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 315d6dd522f3c6be2d36b1eb411d9f471350df60
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182929"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="0d16e-102">CorDebugGCType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0d16e-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="0d16e-103">Atık toplayıcı bir iş istasyonunda veya sunucuda çalışıp çalışmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d16e-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d16e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d16e-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d16e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d16e-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="0d16e-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0d16e-106">Members</span></span>  
  
|<span data-ttu-id="0d16e-107">Üye adı</span><span class="sxs-lookup"><span data-stu-id="0d16e-107">Member name</span></span>|<span data-ttu-id="0d16e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d16e-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="0d16e-109">Çöp toplayıcı, bir iş istasyonunda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="0d16e-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="0d16e-110">Çöp toplayıcı, bir sunucu üzerinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="0d16e-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d16e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d16e-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d16e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d16e-112">Requirements</span></span>  
 <span data-ttu-id="0d16e-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d16e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d16e-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d16e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d16e-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d16e-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0d16e-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="0d16e-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0d16e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d16e-117">See also</span></span>

- [<span data-ttu-id="0d16e-118">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="0d16e-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
