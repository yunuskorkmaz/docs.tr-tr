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
ms.openlocfilehash: 9f2f5af86e210493cd8ba0eb8afe10d22b84b18c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408014"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="77bdd-102">CorDebugDebugEventKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="77bdd-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="77bdd-103">, Bilgileri kodunu çözdü olay türünü gösterir [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77bdd-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77bdd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77bdd-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="77bdd-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="77bdd-105">Members</span></span>  
  
|<span data-ttu-id="77bdd-106">Üye</span><span class="sxs-lookup"><span data-stu-id="77bdd-106">Member</span></span>|<span data-ttu-id="77bdd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77bdd-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="77bdd-108">Bir modül yük olayı.</span><span class="sxs-lookup"><span data-stu-id="77bdd-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="77bdd-109">Bir modül unload olayı.</span><span class="sxs-lookup"><span data-stu-id="77bdd-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="77bdd-110">İlk fırsat özel durum.</span><span class="sxs-lookup"><span data-stu-id="77bdd-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="77bdd-111">Bir kullanıcı ilk fırsat özel durum.</span><span class="sxs-lookup"><span data-stu-id="77bdd-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="77bdd-112">Bir özel durum olan bir `catch` işleyici yok.</span><span class="sxs-lookup"><span data-stu-id="77bdd-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="77bdd-113">İşlenmeyen bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="77bdd-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77bdd-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77bdd-114">Remarks</span></span>  
 <span data-ttu-id="77bdd-115">Üye `CorDebugDebugEventKind` numaralandırma çağırarak döndürülür [Icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77bdd-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77bdd-116">Bu numaralandırma .NET senaryoları yalnızca hata ayıklama yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="77bdd-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77bdd-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77bdd-117">Requirements</span></span>  
 <span data-ttu-id="77bdd-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77bdd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77bdd-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77bdd-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77bdd-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77bdd-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77bdd-121">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77bdd-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77bdd-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77bdd-122">See Also</span></span>  
 [<span data-ttu-id="77bdd-123">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="77bdd-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
