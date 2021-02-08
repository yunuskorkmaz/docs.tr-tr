---
description: 'Şu konuda daha fazla bilgi edinin: Cordebugdebugger Geventkind numaralandırması'
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
ms.openlocfilehash: 62094c934873a74fdab01fad87c42126e28cb0f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801715"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="0c3a7-103">CorDebugDebugEventKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0c3a7-103">CorDebugDebugEventKind Enumeration</span></span>

<span data-ttu-id="0c3a7-104">Bilgileri [DecodeEvent](icordebugprocess6-decodeevent-method.md) yöntemi tarafından kodu çözülen olay türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c3a7-104">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c3a7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0c3a7-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="0c3a7-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0c3a7-106">Members</span></span>  
  
|<span data-ttu-id="0c3a7-107">Üye</span><span class="sxs-lookup"><span data-stu-id="0c3a7-107">Member</span></span>|<span data-ttu-id="0c3a7-108">Description</span><span class="sxs-lookup"><span data-stu-id="0c3a7-108">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="0c3a7-109">Modül yükleme olayı.</span><span class="sxs-lookup"><span data-stu-id="0c3a7-109">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="0c3a7-110">Modül kaldırma olayı.</span><span class="sxs-lookup"><span data-stu-id="0c3a7-110">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="0c3a7-111">Birinci şans özel durumu.</span><span class="sxs-lookup"><span data-stu-id="0c3a7-111">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="0c3a7-112">Birinci şans Kullanıcı özel durumu.</span><span class="sxs-lookup"><span data-stu-id="0c3a7-112">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="0c3a7-113">Bir işleyicinin bulunduğu özel durum `catch` .</span><span class="sxs-lookup"><span data-stu-id="0c3a7-113">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="0c3a7-114">İşlenmeyen bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="0c3a7-114">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c3a7-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c3a7-115">Remarks</span></span>  

 <span data-ttu-id="0c3a7-116">`CorDebugDebugEventKind` [Icordebugdebugger gevent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) yöntemi çağırarak sabit listesinin bir üyesi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0c3a7-116">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c3a7-117">Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0c3a7-117">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c3a7-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c3a7-118">Requirements</span></span>  

 <span data-ttu-id="0c3a7-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c3a7-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c3a7-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0c3a7-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c3a7-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0c3a7-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c3a7-122">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c3a7-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c3a7-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c3a7-123">See also</span></span>

- [<span data-ttu-id="0c3a7-124">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="0c3a7-124">Debugging Enumerations</span></span>](debugging-enumerations.md)
