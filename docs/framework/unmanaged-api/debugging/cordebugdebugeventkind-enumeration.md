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
ms.openlocfilehash: b7db7c9e17d87b91e09d5d010d40431cba5385df
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795995"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="d8392-102">CorDebugDebugEventKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d8392-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="d8392-103">Bilgileri [DecodeEvent](icordebugprocess6-decodeevent-method.md) yöntemi tarafından kodu çözülen olay türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8392-103">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8392-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8392-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d8392-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d8392-105">Members</span></span>  
  
|<span data-ttu-id="d8392-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d8392-106">Member</span></span>|<span data-ttu-id="d8392-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8392-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="d8392-108">Modül yükleme olayı.</span><span class="sxs-lookup"><span data-stu-id="d8392-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="d8392-109">Modül kaldırma olayı.</span><span class="sxs-lookup"><span data-stu-id="d8392-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="d8392-110">Birinci şans özel durumu.</span><span class="sxs-lookup"><span data-stu-id="d8392-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="d8392-111">Birinci şans Kullanıcı özel durumu.</span><span class="sxs-lookup"><span data-stu-id="d8392-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="d8392-112">Bir `catch` işleyicinin bulunduğu özel durum.</span><span class="sxs-lookup"><span data-stu-id="d8392-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="d8392-113">İşlenmeyen bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="d8392-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8392-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8392-114">Remarks</span></span>  
 <span data-ttu-id="d8392-115">`CorDebugDebugEventKind` [Icordebugdebugger gevent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) yöntemi çağırarak sabit listesinin bir üyesi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d8392-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8392-116">Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d8392-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8392-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8392-117">Requirements</span></span>  
 <span data-ttu-id="d8392-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8392-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8392-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d8392-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8392-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d8392-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8392-121">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8392-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8392-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8392-122">See also</span></span>

- [<span data-ttu-id="d8392-123">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="d8392-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
