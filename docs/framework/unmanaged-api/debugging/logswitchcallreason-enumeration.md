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
ms.openlocfilehash: 2a6ca9f4d74c508ac0a2af68c2a5b0a3e6d6b217
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139175"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="af8e6-102">LogSwitchCallReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="af8e6-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="af8e6-103">Hata ayıklama/izleme anahtarı üzerinde gerçekleştirilen işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="af8e6-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af8e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af8e6-104">Syntax</span></span>  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="af8e6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="af8e6-105">Members</span></span>  
  
|<span data-ttu-id="af8e6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="af8e6-106">Member</span></span>|<span data-ttu-id="af8e6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af8e6-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="af8e6-108">Hata ayıklama/izleme anahtarı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="af8e6-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="af8e6-109">Bir hata ayıklama/izleme anahtarı değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="af8e6-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="af8e6-110">Hata ayıklama/izleme anahtarı silindi.</span><span class="sxs-lookup"><span data-stu-id="af8e6-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="af8e6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af8e6-111">Requirements</span></span>  
 <span data-ttu-id="af8e6-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af8e6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af8e6-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="af8e6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af8e6-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="af8e6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af8e6-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af8e6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af8e6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af8e6-116">See also</span></span>

- [<span data-ttu-id="af8e6-117">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="af8e6-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
