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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182929"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="30309-102">CorDebugGCType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="30309-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="30309-103">Atık toplayıcı bir iş istasyonunda veya sunucuda çalışıp çalışmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="30309-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30309-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30309-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="30309-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30309-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="30309-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="30309-106">Members</span></span>  
  
|<span data-ttu-id="30309-107">Üye adı</span><span class="sxs-lookup"><span data-stu-id="30309-107">Member name</span></span>|<span data-ttu-id="30309-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30309-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="30309-109">Çöp toplayıcı, bir iş istasyonunda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="30309-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="30309-110">Çöp toplayıcı, bir sunucu üzerinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="30309-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30309-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30309-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30309-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30309-112">Requirements</span></span>  
 <span data-ttu-id="30309-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30309-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30309-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30309-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30309-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30309-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30309-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30309-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30309-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30309-117">See also</span></span>

- [<span data-ttu-id="30309-118">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="30309-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
