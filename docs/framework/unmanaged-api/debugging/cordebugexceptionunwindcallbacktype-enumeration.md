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
ms.openlocfilehash: 5004cd293b64436c41caef1c7393d2229d1a6ccf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098476"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="a73d0-102">CorDebugExceptionUnwindCallbackType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a73d0-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="a73d0-103">Geriye doğru izleme aşamasında geri çağırma tarafından sinyal edilen olayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a73d0-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a73d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a73d0-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="a73d0-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a73d0-105">Members</span></span>  
  
|<span data-ttu-id="a73d0-106">Üye</span><span class="sxs-lookup"><span data-stu-id="a73d0-106">Member</span></span>|<span data-ttu-id="a73d0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a73d0-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="a73d0-108">Geriye doğru izleme işleminin başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="a73d0-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="a73d0-109">Özel durum yakalanmıştı.</span><span class="sxs-lookup"><span data-stu-id="a73d0-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a73d0-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a73d0-110">Requirements</span></span>  
 <span data-ttu-id="a73d0-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a73d0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a73d0-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a73d0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a73d0-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a73d0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a73d0-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a73d0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a73d0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a73d0-115">See also</span></span>

- [<span data-ttu-id="a73d0-116">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="a73d0-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
