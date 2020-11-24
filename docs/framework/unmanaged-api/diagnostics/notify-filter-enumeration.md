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
ms.openlocfilehash: 365bc0dc73b04d3afd171c40f336432f77552b6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690960"
---
# <a name="notify_filter-enumeration"></a><span data-ttu-id="a7ae1-102">NOTIFY_FILTER Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a7ae1-102">NOTIFY_FILTER Enumeration</span></span>

<span data-ttu-id="a7ae1-103">Hata ayıklayıcı işlevleri için geri çağırmaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7ae1-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="a7ae1-104">Daha fazla bilgi için bkz. [INotifySource2:: SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a7ae1-104">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7ae1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a7ae1-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a7ae1-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a7ae1-106">Members</span></span>  
  
|<span data-ttu-id="a7ae1-107">Üye</span><span class="sxs-lookup"><span data-stu-id="a7ae1-107">Member</span></span>|<span data-ttu-id="a7ae1-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7ae1-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="a7ae1-109">[INotifySink2:: Onsyncbelirtme](inotifysink2-onsynccallout-method.md) yönteminin çağrılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7ae1-109">Indicates that the [INotifySink2::OnSyncCallOut](inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="a7ae1-110">[INotifySink2:: OnSyncCallEnter](inotifysink2-onsynccallenter-method.md) yönteminin çağrılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7ae1-110">Indicates that the [INotifySink2::OnSyncCallEnter](inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="a7ae1-111">[INotifySink2:: OnSyncCallExit](inotifysink2-onsynccallexit-method.md) yönteminin çağrılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7ae1-111">Indicates that the [INotifySink2::OnSyncCallExit](inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="a7ae1-112">[INotifySink2:: OnSyncCallReturn](inotifysink2-onsynccallreturn-method.md) yönteminin çağrılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7ae1-112">Indicates that the [INotifySink2::OnSyncCallReturn](inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="a7ae1-113">Tüm [INotifySink2](inotifysink2-interface.md) yöntemlerinin çağrılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7ae1-113">Indicates that all of the [INotifySink2](inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="a7ae1-114">Tüm mevcut ve gelecekteki bildirimleri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="a7ae1-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="a7ae1-115">Hiçbir bildirim yönteminin çağrılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7ae1-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a7ae1-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7ae1-116">Requirements</span></span>  

 <span data-ttu-id="a7ae1-117">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="a7ae1-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ae1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7ae1-118">See also</span></span>

- [<span data-ttu-id="a7ae1-119">Tanılama Sembol Deposu Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="a7ae1-119">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
