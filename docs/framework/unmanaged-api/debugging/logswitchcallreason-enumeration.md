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
ms.openlocfilehash: 29781666c106755f96f945325e3a8953bf93b211
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790341"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="fcfb8-102">LogSwitchCallReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fcfb8-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="fcfb8-103">Hata ayıklama/izleme anahtarı üzerinde gerçekleştirilen işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="fcfb8-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcfb8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcfb8-104">Syntax</span></span>  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="fcfb8-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fcfb8-105">Members</span></span>  
  
|<span data-ttu-id="fcfb8-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fcfb8-106">Member</span></span>|<span data-ttu-id="fcfb8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcfb8-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="fcfb8-108">Hata ayıklama/izleme anahtarı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="fcfb8-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="fcfb8-109">Bir hata ayıklama/izleme anahtarı değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="fcfb8-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="fcfb8-110">Hata ayıklama/izleme anahtarı silindi.</span><span class="sxs-lookup"><span data-stu-id="fcfb8-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fcfb8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fcfb8-111">Requirements</span></span>  
 <span data-ttu-id="fcfb8-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcfb8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcfb8-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fcfb8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcfb8-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fcfb8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcfb8-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcfb8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcfb8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcfb8-116">See also</span></span>

- [<span data-ttu-id="fcfb8-117">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fcfb8-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
