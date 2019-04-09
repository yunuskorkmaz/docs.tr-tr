---
title: CorDebugDebugEventKind Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugDebugEventKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e5479fad3f19c219a0ca1d5d01934ce92a7162e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127183"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="9a8de-102">CorDebugDebugEventKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9a8de-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="9a8de-103">, Bilgileri kodu çözülen olay türünü gösteren [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9a8de-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a8de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a8de-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="9a8de-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9a8de-105">Members</span></span>  
  
|<span data-ttu-id="9a8de-106">Üye</span><span class="sxs-lookup"><span data-stu-id="9a8de-106">Member</span></span>|<span data-ttu-id="9a8de-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a8de-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="9a8de-108">Modül yükleme olayı.</span><span class="sxs-lookup"><span data-stu-id="9a8de-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="9a8de-109">Modül kaldırma olayı.</span><span class="sxs-lookup"><span data-stu-id="9a8de-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="9a8de-110">İlk fırsat özel durum.</span><span class="sxs-lookup"><span data-stu-id="9a8de-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="9a8de-111">Bir kullanıcı ilk fırsat özel durum.</span><span class="sxs-lookup"><span data-stu-id="9a8de-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="9a8de-112">Kendisi için bir özel durum bir `catch` işleyici yok.</span><span class="sxs-lookup"><span data-stu-id="9a8de-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="9a8de-113">İşlenmeyen bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="9a8de-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a8de-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a8de-114">Remarks</span></span>  
 <span data-ttu-id="9a8de-115">Üye `CorDebugDebugEventKind` numaralandırma çağırarak döndürülür [Icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9a8de-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a8de-116">Bu numaralandırma .NET hata ayıklama senaryoları yalnızca yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="9a8de-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a8de-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a8de-117">Requirements</span></span>  
 <span data-ttu-id="9a8de-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a8de-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a8de-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a8de-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a8de-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a8de-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9a8de-121">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="9a8de-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9a8de-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a8de-122">See also</span></span>

- [<span data-ttu-id="9a8de-123">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="9a8de-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
