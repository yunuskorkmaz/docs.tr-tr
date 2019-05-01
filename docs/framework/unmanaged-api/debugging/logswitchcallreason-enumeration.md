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
ms.openlocfilehash: 7eadb595eb62b4f1a9dcc888225cbb7454119c7c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986550"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="b6325-102">LogSwitchCallReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b6325-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="b6325-103">Hata ayıklama izlemeyi anahtarda gerçekleştirilen bir işlemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6325-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6325-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6325-104">Syntax</span></span>  
  
```  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="b6325-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b6325-105">Members</span></span>  
  
|<span data-ttu-id="b6325-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b6325-106">Member</span></span>|<span data-ttu-id="b6325-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6325-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="b6325-108">Hata ayıklama izleme anahtarı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b6325-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="b6325-109">Hata ayıklama izleme anahtarı değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="b6325-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="b6325-110">Hata ayıklama izleme anahtarı silindi.</span><span class="sxs-lookup"><span data-stu-id="b6325-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6325-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6325-111">Requirements</span></span>  
 <span data-ttu-id="b6325-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6325-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6325-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6325-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6325-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6325-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6325-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6325-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6325-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6325-116">See also</span></span>

- [<span data-ttu-id="b6325-117">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b6325-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
