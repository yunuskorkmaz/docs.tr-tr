---
title: "LogSwitchCallReason Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LogSwitchCallReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: LogSwitchCallReason
helpviewer_keywords: LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 937b26efa79605b585c420db608a938b3ee71f8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="712bc-102">LogSwitchCallReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="712bc-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="712bc-103">Hata ayıklama izleme anahtarı üzerinde gerçekleştirilen işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="712bc-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="712bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="712bc-104">Syntax</span></span>  
  
```  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="712bc-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="712bc-105">Members</span></span>  
  
|<span data-ttu-id="712bc-106">Üye</span><span class="sxs-lookup"><span data-stu-id="712bc-106">Member</span></span>|<span data-ttu-id="712bc-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="712bc-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="712bc-108">Hata ayıklama izleme anahtarı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="712bc-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="712bc-109">Hata ayıklama izleme anahtarı değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="712bc-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="712bc-110">Hata ayıklama izleme anahtarı silindi.</span><span class="sxs-lookup"><span data-stu-id="712bc-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="712bc-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="712bc-111">Requirements</span></span>  
 <span data-ttu-id="712bc-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="712bc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="712bc-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="712bc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="712bc-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="712bc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="712bc-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="712bc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="712bc-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="712bc-116">See Also</span></span>  
 [<span data-ttu-id="712bc-117">Hata ayıklama numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="712bc-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
