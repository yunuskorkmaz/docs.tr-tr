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
ms.openlocfilehash: b20e18d5f4314a0ab1442ac7bd5c6514e4db85d5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609488"
---
# <a name="notify_filter-enumeration"></a><span data-ttu-id="4122a-102">NOTIFY_FILTER Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4122a-102">NOTIFY_FILTER Enumeration</span></span>
<span data-ttu-id="4122a-103">Hata ayıklayıcı işlevleri için geri çağırmaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4122a-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="4122a-104">Daha fazla bilgi için bkz. [INotifySource2:: SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4122a-104">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4122a-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4122a-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="4122a-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4122a-106">Members</span></span>  
  
|<span data-ttu-id="4122a-107">Üye</span><span class="sxs-lookup"><span data-stu-id="4122a-107">Member</span></span>|<span data-ttu-id="4122a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4122a-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="4122a-109">[INotifySink2:: Onsyncbelirtme](inotifysink2-onsynccallout-method.md) yönteminin çağrılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4122a-109">Indicates that the [INotifySink2::OnSyncCallOut](inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="4122a-110">[INotifySink2:: OnSyncCallEnter](inotifysink2-onsynccallenter-method.md) yönteminin çağrılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4122a-110">Indicates that the [INotifySink2::OnSyncCallEnter](inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="4122a-111">[INotifySink2:: OnSyncCallExit](inotifysink2-onsynccallexit-method.md) yönteminin çağrılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4122a-111">Indicates that the [INotifySink2::OnSyncCallExit](inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="4122a-112">[INotifySink2:: OnSyncCallReturn](inotifysink2-onsynccallreturn-method.md) yönteminin çağrılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4122a-112">Indicates that the [INotifySink2::OnSyncCallReturn](inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="4122a-113">Tüm [INotifySink2](inotifysink2-interface.md) yöntemlerinin çağrılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4122a-113">Indicates that all of the [INotifySink2](inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="4122a-114">Tüm mevcut ve gelecekteki bildirimleri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="4122a-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="4122a-115">Hiçbir bildirim yönteminin çağrılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4122a-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4122a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4122a-116">Requirements</span></span>  
 <span data-ttu-id="4122a-117">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="4122a-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4122a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4122a-118">See also</span></span>

- [<span data-ttu-id="4122a-119">Tanılama Simge Deposu Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="4122a-119">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
