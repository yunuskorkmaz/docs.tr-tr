---
description: 'Daha fazla bilgi edinin: CorDebugExceptionFlags numaralandırması'
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
ms.openlocfilehash: c0036c2674f3202623da1a8fdeea14165a2a6e62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747055"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="9b366-103">CorDebugExceptionFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9b366-103">CorDebugExceptionFlags Enumeration</span></span>

<span data-ttu-id="9b366-104">Bir özel durum hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b366-104">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b366-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9b366-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="9b366-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9b366-106">Members</span></span>  
  
|<span data-ttu-id="9b366-107">Üye</span><span class="sxs-lookup"><span data-stu-id="9b366-107">Member</span></span>|<span data-ttu-id="9b366-108">Description</span><span class="sxs-lookup"><span data-stu-id="9b366-108">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="9b366-109">Özel durum yok.</span><span class="sxs-lookup"><span data-stu-id="9b366-109">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="9b366-110">Özel durum, yakabir tablodur.</span><span class="sxs-lookup"><span data-stu-id="9b366-110">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="9b366-111">Özel durumun zamanlaması yine de hata ayıklayıcı tarafından ele ılamıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="9b366-111">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="9b366-112">Örneğin, geçerli geri aramanın altında veya bir tam zamanında (JıT) eki tarafından sonuçlanmış özel durum olayı yoksa, özel durum yakalanamaz.</span><span class="sxs-lookup"><span data-stu-id="9b366-112">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b366-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b366-113">Remarks</span></span>  

 <span data-ttu-id="9b366-114">Yeni değerler sonraki sürümlerde bu numaralandırmaya eklenebilir, bu nedenle beklenmeyen değerler için kullanılan kodu hazırlamanız gerekir `CorDebugExceptionFlags` .</span><span class="sxs-lookup"><span data-stu-id="9b366-114">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b366-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b366-115">Requirements</span></span>  

 <span data-ttu-id="9b366-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b366-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b366-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9b366-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b366-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9b366-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b366-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b366-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b366-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b366-120">See also</span></span>

- [<span data-ttu-id="9b366-121">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="9b366-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
