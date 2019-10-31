---
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
ms.openlocfilehash: c927dcde99f5217ee7c160359385e0b953034380
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132235"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="4e59c-102">CorDebugExceptionCallbackType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4e59c-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="4e59c-103">Bir [ICorDebugManagedCallback2:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) olayından yapılan geri aramanın türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e59c-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e59c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e59c-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="4e59c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4e59c-105">Members</span></span>  
  
|<span data-ttu-id="4e59c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4e59c-106">Member</span></span>|<span data-ttu-id="4e59c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e59c-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="4e59c-108">Özel durum oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="4e59c-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="4e59c-109">İşlem için Kullanıcı kodu girilen özel durum.</span><span class="sxs-lookup"><span data-stu-id="4e59c-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="4e59c-110">Özel durum, Kullanıcı kodunda bir `catch` bloğu buldu.</span><span class="sxs-lookup"><span data-stu-id="4e59c-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="4e59c-111">Özel durum işlenmedi.</span><span class="sxs-lookup"><span data-stu-id="4e59c-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e59c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e59c-112">Requirements</span></span>  
 <span data-ttu-id="4e59c-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e59c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e59c-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4e59c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e59c-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4e59c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e59c-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e59c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e59c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e59c-117">See also</span></span>

- [<span data-ttu-id="4e59c-118">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="4e59c-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
