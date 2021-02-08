---
description: 'Daha fazla bilgi edinin: CorDebugExceptionCallbackType numaralandırması'
title: CorDebugExceptionCallbackType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugExceptionCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionCallbackType
helpviewer_keywords:
- CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type:
- apiref
ms.openlocfilehash: 41b9cdf707de017703ee3756b3d04a38163bb03b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801689"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="23ad0-103">CorDebugExceptionCallbackType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="23ad0-103">CorDebugExceptionCallbackType Enumeration</span></span>

<span data-ttu-id="23ad0-104">Bir [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) olayından yapılan geri aramanın türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="23ad0-104">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23ad0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="23ad0-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="23ad0-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="23ad0-106">Members</span></span>  
  
|<span data-ttu-id="23ad0-107">Üye</span><span class="sxs-lookup"><span data-stu-id="23ad0-107">Member</span></span>|<span data-ttu-id="23ad0-108">Description</span><span class="sxs-lookup"><span data-stu-id="23ad0-108">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="23ad0-109">Özel durum oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="23ad0-109">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="23ad0-110">İşlem için Kullanıcı kodu girilen özel durum.</span><span class="sxs-lookup"><span data-stu-id="23ad0-110">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="23ad0-111">Bu özel durum, `catch` Kullanıcı kodunda bir blok buldu.</span><span class="sxs-lookup"><span data-stu-id="23ad0-111">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="23ad0-112">Özel durum işlenmedi.</span><span class="sxs-lookup"><span data-stu-id="23ad0-112">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23ad0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23ad0-113">Requirements</span></span>  

 <span data-ttu-id="23ad0-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23ad0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23ad0-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="23ad0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23ad0-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="23ad0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23ad0-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23ad0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ad0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23ad0-118">See also</span></span>

- [<span data-ttu-id="23ad0-119">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="23ad0-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
