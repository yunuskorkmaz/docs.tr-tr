---
title: CorDebugDecodeEventFlagsWindows Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d4e006a03db5b16de93dfd07ec7b964db4bfc1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609223"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="7df89-102">CorDebugDecodeEventFlagsWindows Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7df89-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="7df89-103">Hata ayıklama olaylar hakkında ek bilgi için Windows platformunda sağlar.</span><span class="sxs-lookup"><span data-stu-id="7df89-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7df89-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7df89-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="7df89-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7df89-105">Members</span></span>  
  
|<span data-ttu-id="7df89-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7df89-106">Member</span></span>|<span data-ttu-id="7df89-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7df89-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="7df89-108">Hata ayıklama olayı ilk fırsat özel durum olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7df89-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7df89-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7df89-109">Remarks</span></span>  
 <span data-ttu-id="7df89-110">[Icordebugprocess6::decodeevent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi içeren bir `dwFlags` hata ayıklama olay hakkında ek bilgi sağlayan ve değeri hedef mimarisine bağımlı olan parametre.</span><span class="sxs-lookup"><span data-stu-id="7df89-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="7df89-111">`CorDebugDecodeEventFlagsWindows` Numaralandırma, Windows platformunda hata ayıklama olayları ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7df89-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7df89-112">Bu numaralandırma .NET hata ayıklama senaryoları yalnızca yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="7df89-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7df89-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7df89-113">Requirements</span></span>  
 <span data-ttu-id="7df89-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7df89-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7df89-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7df89-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7df89-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7df89-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7df89-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7df89-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7df89-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7df89-118">See also</span></span>

- [<span data-ttu-id="7df89-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7df89-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
