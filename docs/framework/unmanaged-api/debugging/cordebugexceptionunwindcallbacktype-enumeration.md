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
ms.openlocfilehash: ef3f1d5e78efe37070bb2bdd6d2834178947af7b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740080"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="ade10-102">CorDebugExceptionUnwindCallbackType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ade10-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="ade10-103">Geri çağırma tarafından geriye doğru izleme aşamasında sinyal olay gösterir.</span><span class="sxs-lookup"><span data-stu-id="ade10-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ade10-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ade10-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="ade10-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ade10-105">Members</span></span>  
  
|<span data-ttu-id="ade10-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ade10-106">Member</span></span>|<span data-ttu-id="ade10-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ade10-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="ade10-108">Geriye doğru izleme işlemi başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="ade10-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="ade10-109">Özel durum kesildi.</span><span class="sxs-lookup"><span data-stu-id="ade10-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ade10-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ade10-110">Requirements</span></span>  
 <span data-ttu-id="ade10-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ade10-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ade10-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ade10-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ade10-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ade10-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ade10-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ade10-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade10-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ade10-115">See also</span></span>

- [<span data-ttu-id="ade10-116">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ade10-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
