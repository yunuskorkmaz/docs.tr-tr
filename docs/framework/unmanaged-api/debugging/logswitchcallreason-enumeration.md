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
ms.openlocfilehash: 6fe5710f1be0bfa4e651668e2469c3551ad79261
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423838"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="c3cc2-102">LogSwitchCallReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c3cc2-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="c3cc2-103">Hata ayıklama izleme anahtarı üzerinde gerçekleştirilen işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3cc2-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3cc2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3cc2-104">Syntax</span></span>  
  
```  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="c3cc2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c3cc2-105">Members</span></span>  
  
|<span data-ttu-id="c3cc2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c3cc2-106">Member</span></span>|<span data-ttu-id="c3cc2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3cc2-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="c3cc2-108">Hata ayıklama izleme anahtarı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="c3cc2-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="c3cc2-109">Hata ayıklama izleme anahtarı değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="c3cc2-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="c3cc2-110">Hata ayıklama izleme anahtarı silindi.</span><span class="sxs-lookup"><span data-stu-id="c3cc2-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c3cc2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3cc2-111">Requirements</span></span>  
 <span data-ttu-id="c3cc2-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3cc2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3cc2-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3cc2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3cc2-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3cc2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3cc2-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3cc2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3cc2-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c3cc2-116">See Also</span></span>  
 [<span data-ttu-id="c3cc2-117">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c3cc2-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
