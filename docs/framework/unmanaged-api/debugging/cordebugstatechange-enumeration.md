---
title: "CorDebugStateChange Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugStateChange
api_location: mscordbi.dll
api_type: COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: caf49621342be0ff85ac3cb56b95bb87f524c3be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="c7b62-102">CorDebugStateChange Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c7b62-102">CorDebugStateChange Enumeration</span></span>
<span data-ttu-id="c7b62-103">Değişiklikleri işleme dayalı atılan gerekir önbelleğe alınan veri miktarı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7b62-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7b62-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7b62-104">Syntax</span></span>  
  
```  
typedef enum CorDebugStateChange  
{  
    PROCESS_RUNNING = 0x0000001,   
    FLUSH_ALL       = 0x0000002,   
} CorDebugStateChange;  
```  
  
## <a name="members"></a><span data-ttu-id="c7b62-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c7b62-105">Members</span></span>  
  
|<span data-ttu-id="c7b62-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c7b62-106">Member</span></span>|<span data-ttu-id="c7b62-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7b62-107">Description</span></span>|  
|------------|-----------------|  
|`PROCESS_RUNNING`|<span data-ttu-id="c7b62-108">İşlem ileriye doğru yürütme aracılığıyla yeni bir bellek durum sınırına ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="c7b62-108">The process reached a new memory state via forward execution.</span></span>|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|<span data-ttu-id="c7b62-109">İşlem bellek öncekinden daha rasgele farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7b62-109">The process' memory may be arbitrarily different than it was previously.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7b62-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7b62-110">Remarks</span></span>  
 <span data-ttu-id="c7b62-111">Üye `CorDebugStateChange` numaralandırma, bağımsız değişken olarak sağlanır, hata ayıklayıcı çağırdığında [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7b62-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) method</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7b62-112">Bu numaralandırma .NET senaryoları yalnızca hata ayıklama yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="c7b62-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7b62-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7b62-113">Requirements</span></span>  
 <span data-ttu-id="c7b62-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7b62-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7b62-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7b62-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7b62-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7b62-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7b62-117">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7b62-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7b62-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7b62-118">See Also</span></span>  
 [<span data-ttu-id="c7b62-119">Hata ayıklama numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="c7b62-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="c7b62-120">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c7b62-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
