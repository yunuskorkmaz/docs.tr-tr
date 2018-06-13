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
ms.openlocfilehash: 7fe2fcf10b517f4eb7b1c7e87142afb386821246
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404130"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="fa2bd-102">CorDebugExceptionUnwindCallbackType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fa2bd-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="fa2bd-103">Geri çağırma göre geriye doğru izleme aşamasında işaret olay gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa2bd-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa2bd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa2bd-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="fa2bd-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fa2bd-105">Members</span></span>  
  
|<span data-ttu-id="fa2bd-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fa2bd-106">Member</span></span>|<span data-ttu-id="fa2bd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa2bd-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="fa2bd-108">Bırakma işlemi başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="fa2bd-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="fa2bd-109">Özel durum ele.</span><span class="sxs-lookup"><span data-stu-id="fa2bd-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fa2bd-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa2bd-110">Requirements</span></span>  
 <span data-ttu-id="fa2bd-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa2bd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa2bd-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa2bd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa2bd-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa2bd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa2bd-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa2bd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa2bd-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa2bd-115">See Also</span></span>  
 [<span data-ttu-id="fa2bd-116">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fa2bd-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
