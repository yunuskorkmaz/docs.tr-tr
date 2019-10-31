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
ms.openlocfilehash: de4ac1f39ea9cfb4b616bd4e2c85e5de530dbb0b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132226"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="022de-102">CorDebugDebugEventKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="022de-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="022de-103">Bilgileri [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi tarafından kodu çözülen olay türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="022de-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="022de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="022de-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="022de-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="022de-105">Members</span></span>  
  
|<span data-ttu-id="022de-106">Üye</span><span class="sxs-lookup"><span data-stu-id="022de-106">Member</span></span>|<span data-ttu-id="022de-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="022de-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="022de-108">Modül yükleme olayı.</span><span class="sxs-lookup"><span data-stu-id="022de-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="022de-109">Modül kaldırma olayı.</span><span class="sxs-lookup"><span data-stu-id="022de-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="022de-110">Birinci şans özel durumu.</span><span class="sxs-lookup"><span data-stu-id="022de-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="022de-111">Birinci şans Kullanıcı özel durumu.</span><span class="sxs-lookup"><span data-stu-id="022de-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="022de-112">`catch` işleyicisi bulunan bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="022de-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="022de-113">İşlenmeyen bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="022de-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="022de-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="022de-114">Remarks</span></span>  
 <span data-ttu-id="022de-115">`CorDebugDebugEventKind` numaralandırmanın bir üyesi [ıcordebugdebugger gevent:: GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) yöntemi çağırarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="022de-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="022de-116">Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="022de-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="022de-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="022de-117">Requirements</span></span>  
 <span data-ttu-id="022de-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="022de-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="022de-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="022de-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="022de-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="022de-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="022de-121">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="022de-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="022de-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="022de-122">See also</span></span>

- [<span data-ttu-id="022de-123">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="022de-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
