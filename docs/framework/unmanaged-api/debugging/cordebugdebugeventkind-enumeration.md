---
title: "CorDebugDebugEventKind Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugDebugEventKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 90cd2b8d02cb1d16e4932ffdcc3c9b02dc71541a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="89233-102">CorDebugDebugEventKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="89233-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="89233-103">, Bilgileri kodunu çözdü olay türünü gösterir [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="89233-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89233-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89233-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="89233-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="89233-105">Members</span></span>  
  
|<span data-ttu-id="89233-106">Üye</span><span class="sxs-lookup"><span data-stu-id="89233-106">Member</span></span>|<span data-ttu-id="89233-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89233-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="89233-108">Bir modül yük olayı.</span><span class="sxs-lookup"><span data-stu-id="89233-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="89233-109">Bir modül unload olayı.</span><span class="sxs-lookup"><span data-stu-id="89233-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="89233-110">İlk fırsat özel durum.</span><span class="sxs-lookup"><span data-stu-id="89233-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="89233-111">Bir kullanıcı ilk fırsat özel durum.</span><span class="sxs-lookup"><span data-stu-id="89233-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="89233-112">Bir özel durum olan bir `catch` işleyici yok.</span><span class="sxs-lookup"><span data-stu-id="89233-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="89233-113">İşlenmeyen bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="89233-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89233-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89233-114">Remarks</span></span>  
 <span data-ttu-id="89233-115">Üye `CorDebugDebugEventKind` numaralandırma çağırarak döndürülür [Icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="89233-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89233-116">Bu numaralandırma .NET senaryoları yalnızca hata ayıklama yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="89233-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89233-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89233-117">Requirements</span></span>  
 <span data-ttu-id="89233-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89233-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89233-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89233-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89233-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89233-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89233-121">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89233-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89233-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="89233-122">See Also</span></span>  
 [<span data-ttu-id="89233-123">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="89233-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
