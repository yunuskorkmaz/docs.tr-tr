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
ms.openlocfilehash: 63c3ecd0ae0d9e1df62d73eb05b759093583f652
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142889"
---
# <a name="notifyfilter-enumeration"></a><span data-ttu-id="6ec72-102">NOTIFY_FILTER Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6ec72-102">NOTIFY_FILTER Enumeration</span></span>
<span data-ttu-id="6ec72-103">Hata ayıklayıcı işlevleri için geri çağırmaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6ec72-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="6ec72-104">Daha fazla bilgi için [Inotifysource2::setnotifyfilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6ec72-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ec72-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ec72-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="6ec72-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6ec72-106">Members</span></span>  
  
|<span data-ttu-id="6ec72-107">Üye</span><span class="sxs-lookup"><span data-stu-id="6ec72-107">Member</span></span>|<span data-ttu-id="6ec72-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ec72-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="6ec72-109">Bildiren [Inotifysink2::onsynccallout](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) yöntemi çağrılacak.</span><span class="sxs-lookup"><span data-stu-id="6ec72-109">Indicates that the [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="6ec72-110">Bildiren [Inotifysink2::onsynccallenter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) yöntemi çağrılacak.</span><span class="sxs-lookup"><span data-stu-id="6ec72-110">Indicates that the [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="6ec72-111">Bildiren [Inotifysink2::onsynccallexit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) yöntemi çağrılacak.</span><span class="sxs-lookup"><span data-stu-id="6ec72-111">Indicates that the [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="6ec72-112">Bildiren [Inotifysink2::onsynccallreturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) yöntemi çağrılacak.</span><span class="sxs-lookup"><span data-stu-id="6ec72-112">Indicates that the [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="6ec72-113">Bildiren tüm [Inotifysink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) yöntemleri çağrılacak.</span><span class="sxs-lookup"><span data-stu-id="6ec72-113">Indicates that all of the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="6ec72-114">Tüm mevcut ve gelecekteki bildirimleri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="6ec72-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="6ec72-115">Hiçbir bildirim yöntemi çağrılmalıdır gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ec72-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6ec72-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ec72-116">Requirements</span></span>  
 <span data-ttu-id="6ec72-117">**Üst bilgi:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="6ec72-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ec72-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ec72-118">See also</span></span>

- [<span data-ttu-id="6ec72-119">Tanılama Simge Deposu Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="6ec72-119">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
