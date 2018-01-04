---
title: CorDebugGCType Sabit Listesi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugGCType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugGCType
helpviewer_keywords: CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2045c2edd129c2e4154d24b43d96f6ea8ad64cab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="16591-102">CorDebugGCType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="16591-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="16591-103">Çöp toplayıcı bir iş istasyonunda veya sunucuda çalışıp çalışmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="16591-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16591-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16591-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16591-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16591-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="16591-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="16591-106">Members</span></span>  
  
|<span data-ttu-id="16591-107">Üye adı</span><span class="sxs-lookup"><span data-stu-id="16591-107">Member name</span></span>|<span data-ttu-id="16591-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16591-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="16591-109">Çöp toplayıcı bir iş istasyonunda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="16591-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="16591-110">Çöp toplayıcı bir sunucu üzerinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="16591-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16591-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16591-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16591-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16591-112">Requirements</span></span>  
 <span data-ttu-id="16591-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16591-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16591-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16591-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16591-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16591-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16591-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16591-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16591-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16591-117">See Also</span></span>  
 [<span data-ttu-id="16591-118">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="16591-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
