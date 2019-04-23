---
title: CorDebugExceptionFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugExceptionFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionFlags
helpviewer_keywords:
- CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c7b9b25673685dde8b75702c80f525515917ae1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078713"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="473f1-102">CorDebugExceptionFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="473f1-102">CorDebugExceptionFlags Enumeration</span></span>
<span data-ttu-id="473f1-103">Bir özel durum hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="473f1-103">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="473f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="473f1-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="473f1-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="473f1-105">Members</span></span>  
  
|<span data-ttu-id="473f1-106">Üye</span><span class="sxs-lookup"><span data-stu-id="473f1-106">Member</span></span>|<span data-ttu-id="473f1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="473f1-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="473f1-108">Hiçbir özel durum söz konusudur.</span><span class="sxs-lookup"><span data-stu-id="473f1-108">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="473f1-109">İnterceptable istisnadır.</span><span class="sxs-lookup"><span data-stu-id="473f1-109">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="473f1-110">Hata ayıklayıcı müdahale edemez, özel durumun zamanlamayı yine de olabilir.</span><span class="sxs-lookup"><span data-stu-id="473f1-110">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="473f1-111">Örneğin, geçerli bir geri çağırma aşağıda Yönetilen kod yok ya da özel durum olayı just-ın-time (JIT) ekten sonuçlandı. özel durum müdahale edilebilir olamaz.</span><span class="sxs-lookup"><span data-stu-id="473f1-111">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="473f1-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="473f1-112">Remarks</span></span>  
 <span data-ttu-id="473f1-113">Yeni değerler eklenebilir sonraki sürümlerinde bu sabit listesi için kullanan kodu hazırlamanız şekilde `CorDebugExceptionFlags` için beklenmeyen değer.</span><span class="sxs-lookup"><span data-stu-id="473f1-113">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="473f1-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="473f1-114">Requirements</span></span>  
 <span data-ttu-id="473f1-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="473f1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="473f1-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="473f1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="473f1-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="473f1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="473f1-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="473f1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="473f1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="473f1-119">See also</span></span>

- [<span data-ttu-id="473f1-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="473f1-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
