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
ms.openlocfilehash: 4d29bb3886ffb51e1dfb9654f4d70ef7c568fd43
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420714"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="7b2ff-102">LogSwitchCallReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7b2ff-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="7b2ff-103">Hata ayıklama/izleme anahtarı üzerinde gerçekleştirilen işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b2ff-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b2ff-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7b2ff-104">Syntax</span></span>  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="7b2ff-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7b2ff-105">Members</span></span>  
  
|<span data-ttu-id="7b2ff-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7b2ff-106">Member</span></span>|<span data-ttu-id="7b2ff-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b2ff-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="7b2ff-108">Hata ayıklama/izleme anahtarı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="7b2ff-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="7b2ff-109">Bir hata ayıklama/izleme anahtarı değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="7b2ff-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="7b2ff-110">Hata ayıklama/izleme anahtarı silindi.</span><span class="sxs-lookup"><span data-stu-id="7b2ff-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7b2ff-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b2ff-111">Requirements</span></span>  
 <span data-ttu-id="7b2ff-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b2ff-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b2ff-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7b2ff-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b2ff-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7b2ff-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b2ff-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b2ff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b2ff-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b2ff-116">See also</span></span>

- [<span data-ttu-id="7b2ff-117">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="7b2ff-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
