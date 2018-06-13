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
ms.openlocfilehash: d963a478ee7ae42159a0eb8a4b41cf20ae663aa5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405463"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="225f9-102">CorDebugExceptionFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="225f9-102">CorDebugExceptionFlags Enumeration</span></span>
<span data-ttu-id="225f9-103">Bir özel durum hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="225f9-103">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="225f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="225f9-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="225f9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="225f9-105">Members</span></span>  
  
|<span data-ttu-id="225f9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="225f9-106">Member</span></span>|<span data-ttu-id="225f9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="225f9-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="225f9-108">Hiçbir özel durum yoktur.</span><span class="sxs-lookup"><span data-stu-id="225f9-108">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="225f9-109">Özel durum interceptable kullanılır.</span><span class="sxs-lookup"><span data-stu-id="225f9-109">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="225f9-110">Hata ayıklayıcı müdahale edemez şekilde özel zamanlama hala olabilir.</span><span class="sxs-lookup"><span data-stu-id="225f9-110">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="225f9-111">Örneğin, yönetilen kodu geçerli geri çağırma aşağıda yok veya tam zamanında (JIT) ekten özel durum olayı sonuçlandı, özel durum ele geçirilebilecek olamaz.</span><span class="sxs-lookup"><span data-stu-id="225f9-111">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="225f9-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="225f9-112">Remarks</span></span>  
 <span data-ttu-id="225f9-113">Yeni değerler eklenebilir sonraki sürümlerinde, bu numaralandırma için kullanan kodu hazırlamalısınız şekilde `CorDebugExceptionFlags` için beklenmeyen değer.</span><span class="sxs-lookup"><span data-stu-id="225f9-113">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="225f9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="225f9-114">Requirements</span></span>  
 <span data-ttu-id="225f9-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="225f9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="225f9-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="225f9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="225f9-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="225f9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="225f9-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="225f9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="225f9-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="225f9-119">See Also</span></span>  
 [<span data-ttu-id="225f9-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="225f9-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
