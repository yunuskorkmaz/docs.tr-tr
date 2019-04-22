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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127183"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="30852-102">CorDebugDebugEventKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="30852-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="30852-103">, Bilgileri kodu çözülen olay türünü gösteren [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="30852-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30852-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30852-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="30852-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="30852-105">Members</span></span>  
  
|<span data-ttu-id="30852-106">Üye</span><span class="sxs-lookup"><span data-stu-id="30852-106">Member</span></span>|<span data-ttu-id="30852-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30852-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="30852-108">Modül yükleme olayı.</span><span class="sxs-lookup"><span data-stu-id="30852-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="30852-109">Modül kaldırma olayı.</span><span class="sxs-lookup"><span data-stu-id="30852-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="30852-110">İlk fırsat özel durum.</span><span class="sxs-lookup"><span data-stu-id="30852-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="30852-111">Bir kullanıcı ilk fırsat özel durum.</span><span class="sxs-lookup"><span data-stu-id="30852-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="30852-112">Kendisi için bir özel durum bir `catch` işleyici yok.</span><span class="sxs-lookup"><span data-stu-id="30852-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="30852-113">İşlenmeyen bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="30852-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30852-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30852-114">Remarks</span></span>  
 <span data-ttu-id="30852-115">Üye `CorDebugDebugEventKind` numaralandırma çağırarak döndürülür [Icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="30852-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30852-116">Bu numaralandırma .NET hata ayıklama senaryoları yalnızca yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="30852-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30852-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30852-117">Requirements</span></span>  
 <span data-ttu-id="30852-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30852-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30852-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30852-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30852-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30852-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30852-121">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30852-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30852-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30852-122">See also</span></span>

- [<span data-ttu-id="30852-123">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="30852-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
