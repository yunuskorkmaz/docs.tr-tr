---
title: CorDebugExceptionUnwindCallbackType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugExceptionUnwindCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionUnwindCallbackType
helpviewer_keywords:
- CorDebugExceptionUnwindCallbackType enumeration [.NET Framework debugging]
ms.assetid: 783dce92-8a98-43db-8f78-888d943dd5b2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408e72eeaa1dac83c45488d186425f30c6043280
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155629"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="7b189-102">CorDebugExceptionUnwindCallbackType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7b189-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="7b189-103">Geri çağırma tarafından geriye doğru izleme aşamasında sinyal olay gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b189-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b189-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b189-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="7b189-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7b189-105">Members</span></span>  
  
|<span data-ttu-id="7b189-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7b189-106">Member</span></span>|<span data-ttu-id="7b189-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b189-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="7b189-108">Geriye doğru izleme işlemi başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="7b189-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="7b189-109">Özel durum kesildi.</span><span class="sxs-lookup"><span data-stu-id="7b189-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7b189-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b189-110">Requirements</span></span>  
 <span data-ttu-id="7b189-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b189-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b189-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b189-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b189-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b189-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7b189-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="7b189-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7b189-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b189-115">See also</span></span>

- [<span data-ttu-id="7b189-116">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="7b189-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
