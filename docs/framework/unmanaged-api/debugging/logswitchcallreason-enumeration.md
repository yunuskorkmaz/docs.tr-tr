---
title: LogSwitchCallReason Numaralandırması
ms.date: 03/30/2017
api_name:
- LogSwitchCallReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LogSwitchCallReason
helpviewer_keywords:
- LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 894f74f12de7ed0754dcca34eacb815efc33c766
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752579"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="6bc6b-102">LogSwitchCallReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6bc6b-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="6bc6b-103">Hata ayıklama izlemeyi anahtarda gerçekleştirilen bir işlemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="6bc6b-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bc6b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6bc6b-104">Syntax</span></span>  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="6bc6b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6bc6b-105">Members</span></span>  
  
|<span data-ttu-id="6bc6b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6bc6b-106">Member</span></span>|<span data-ttu-id="6bc6b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bc6b-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="6bc6b-108">Hata ayıklama izleme anahtarı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6bc6b-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="6bc6b-109">Hata ayıklama izleme anahtarı değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="6bc6b-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="6bc6b-110">Hata ayıklama izleme anahtarı silindi.</span><span class="sxs-lookup"><span data-stu-id="6bc6b-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6bc6b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bc6b-111">Requirements</span></span>  
 <span data-ttu-id="6bc6b-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bc6b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bc6b-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bc6b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bc6b-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bc6b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bc6b-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bc6b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc6b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bc6b-116">See also</span></span>

- [<span data-ttu-id="6bc6b-117">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="6bc6b-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
