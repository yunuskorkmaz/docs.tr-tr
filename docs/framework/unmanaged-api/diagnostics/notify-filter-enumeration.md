---
title: NOTIFY_FILTER Numaralandırması
ms.date: 03/30/2017
api_name:
- NOTIFY_FILTER
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- NOTIFY_FILTER
helpviewer_keywords:
- NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98c3e1ed3da209cbded5d76d938d2420fce606be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431026"
---
# <a name="notifyfilter-enumeration"></a><span data-ttu-id="a3b98-102">NOTIFY_FILTER Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a3b98-102">NOTIFY_FILTER Enumeration</span></span>
<span data-ttu-id="a3b98-103">Hata ayıklayıcı işlevleri için geri çağırmaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a3b98-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="a3b98-104">Daha fazla bilgi için bkz: [Inotifysource2::setnotifyfilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a3b98-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3b98-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3b98-105">Syntax</span></span>  
  
```  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a><span data-ttu-id="a3b98-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a3b98-106">Members</span></span>  
  
|<span data-ttu-id="a3b98-107">Üye</span><span class="sxs-lookup"><span data-stu-id="a3b98-107">Member</span></span>|<span data-ttu-id="a3b98-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3b98-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="a3b98-109">Belirten [Inotifysink2::onsynccallout](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) yöntemi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a3b98-109">Indicates that the [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="a3b98-110">Belirten [Inotifysink2::onsynccallenter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) yöntemi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a3b98-110">Indicates that the [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="a3b98-111">Belirten [Inotifysink2::onsynccallexit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) yöntemi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a3b98-111">Indicates that the [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="a3b98-112">Belirten [Inotifysink2::onsynccallreturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) yöntemi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a3b98-112">Indicates that the [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="a3b98-113">Bildiren tüm [Inotifysink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) yöntemleri çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a3b98-113">Indicates that all of the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="a3b98-114">Tüm mevcut ve gelecekteki bildirimleri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="a3b98-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="a3b98-115">Hiçbir bildirim yöntemi çağrılmalıdır gösterir.</span><span class="sxs-lookup"><span data-stu-id="a3b98-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a3b98-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3b98-116">Requirements</span></span>  
 <span data-ttu-id="a3b98-117">**Başlık:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="a3b98-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3b98-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a3b98-118">See Also</span></span>  
 [<span data-ttu-id="a3b98-119">Tanılama Simge Deposu Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="a3b98-119">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
