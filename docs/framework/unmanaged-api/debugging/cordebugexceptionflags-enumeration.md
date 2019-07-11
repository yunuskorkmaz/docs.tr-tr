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
ms.openlocfilehash: 352a45a33a109570f100e91a24cd44dc4f6780e7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740153"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="dee3d-102">CorDebugExceptionFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="dee3d-102">CorDebugExceptionFlags Enumeration</span></span>
<span data-ttu-id="dee3d-103">Bir özel durum hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dee3d-103">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dee3d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dee3d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="dee3d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="dee3d-105">Members</span></span>  
  
|<span data-ttu-id="dee3d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="dee3d-106">Member</span></span>|<span data-ttu-id="dee3d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dee3d-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="dee3d-108">Hiçbir özel durum söz konusudur.</span><span class="sxs-lookup"><span data-stu-id="dee3d-108">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="dee3d-109">İnterceptable istisnadır.</span><span class="sxs-lookup"><span data-stu-id="dee3d-109">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="dee3d-110">Hata ayıklayıcı müdahale edemez, özel durumun zamanlamayı yine de olabilir.</span><span class="sxs-lookup"><span data-stu-id="dee3d-110">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="dee3d-111">Örneğin, geçerli bir geri çağırma aşağıda Yönetilen kod yok ya da özel durum olayı just-ın-time (JIT) ekten sonuçlandı. özel durum müdahale edilebilir olamaz.</span><span class="sxs-lookup"><span data-stu-id="dee3d-111">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dee3d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dee3d-112">Remarks</span></span>  
 <span data-ttu-id="dee3d-113">Yeni değerler eklenebilir sonraki sürümlerinde bu sabit listesi için kullanan kodu hazırlamanız şekilde `CorDebugExceptionFlags` için beklenmeyen değer.</span><span class="sxs-lookup"><span data-stu-id="dee3d-113">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dee3d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dee3d-114">Requirements</span></span>  
 <span data-ttu-id="dee3d-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dee3d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dee3d-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dee3d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dee3d-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dee3d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dee3d-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dee3d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee3d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dee3d-119">See also</span></span>

- [<span data-ttu-id="dee3d-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="dee3d-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
