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
ms.openlocfilehash: 45de821dd52f7e153fc79ffde056ed959c654fce
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795969"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="7c93c-102">CorDebugExceptionFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7c93c-102">CorDebugExceptionFlags Enumeration</span></span>
<span data-ttu-id="7c93c-103">Bir özel durum hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c93c-103">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c93c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c93c-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="7c93c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7c93c-105">Members</span></span>  
  
|<span data-ttu-id="7c93c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7c93c-106">Member</span></span>|<span data-ttu-id="7c93c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c93c-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="7c93c-108">Özel durum yok.</span><span class="sxs-lookup"><span data-stu-id="7c93c-108">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="7c93c-109">Özel durum, yakabir tablodur.</span><span class="sxs-lookup"><span data-stu-id="7c93c-109">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="7c93c-110">Özel durumun zamanlaması yine de hata ayıklayıcı tarafından ele ılamıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="7c93c-110">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="7c93c-111">Örneğin, geçerli geri aramanın altında veya bir tam zamanında (JıT) eki tarafından sonuçlanmış özel durum olayı yoksa, özel durum yakalanamaz.</span><span class="sxs-lookup"><span data-stu-id="7c93c-111">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c93c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c93c-112">Remarks</span></span>  
 <span data-ttu-id="7c93c-113">Yeni değerler sonraki sürümlerde bu numaralandırmaya eklenebilir, bu nedenle beklenmeyen değerler için kullanılan `CorDebugExceptionFlags` kodu hazırlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7c93c-113">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c93c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c93c-114">Requirements</span></span>  
 <span data-ttu-id="7c93c-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c93c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c93c-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7c93c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c93c-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7c93c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c93c-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c93c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c93c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c93c-119">See also</span></span>

- [<span data-ttu-id="7c93c-120">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="7c93c-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
