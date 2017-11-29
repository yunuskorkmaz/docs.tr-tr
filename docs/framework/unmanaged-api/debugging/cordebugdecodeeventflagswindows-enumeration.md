---
title: "CorDebugDecodeEventFlagsWindows Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugDecodeEventFlagsWindows
api_location: mscordbi.dll
api_type: COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: facde76ec24d90795de7dfb70bfe5772a6f21531
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="a124c-102">CorDebugDecodeEventFlagsWindows Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a124c-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="a124c-103">Hata ayıklama olaylar hakkında ek bilgi Windows platformunda sağlar.</span><span class="sxs-lookup"><span data-stu-id="a124c-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a124c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a124c-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="a124c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a124c-105">Members</span></span>  
  
|<span data-ttu-id="a124c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="a124c-106">Member</span></span>|<span data-ttu-id="a124c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a124c-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="a124c-108">Hata ayıklama olayı ilk fırsat özel durum olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a124c-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a124c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a124c-109">Remarks</span></span>  
 <span data-ttu-id="a124c-110">[Icordebugprocess6::decodeevent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi içeren bir `dwFlags` hata ayıklama olayla ilgili ek bilgi sağlar ve değeri hedef mimarisine bağımlı olan parametre.</span><span class="sxs-lookup"><span data-stu-id="a124c-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="a124c-111">`CorDebugDecodeEventFlagsWindows` Numaralandırma, Windows platformunda hata ayıklama olaylarla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a124c-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a124c-112">Bu numaralandırma .NET senaryoları yalnızca hata ayıklama yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="a124c-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a124c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a124c-113">Requirements</span></span>  
 <span data-ttu-id="a124c-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a124c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a124c-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a124c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a124c-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a124c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a124c-117">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a124c-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a124c-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a124c-118">See Also</span></span>  
 [<span data-ttu-id="a124c-119">Hata ayıklama numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="a124c-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
