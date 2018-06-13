---
title: INotifySource2::SetNotifyFilter Yöntemi
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7a2391527a7912c5def593438a71ed006955e8d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426152"
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="1d841-102">INotifySource2::SetNotifyFilter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d841-102">INotifySource2::SetNotifyFilter Method</span></span>
<span data-ttu-id="1d841-103">Bu kaynak ile kullanmak için bir bildirim filtre atar.</span><span class="sxs-lookup"><span data-stu-id="1d841-103">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d841-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d841-104">Syntax</span></span>  
  
```  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d841-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1d841-105">Parameters</span></span>  
 `in_NotifyFilter`  
 <span data-ttu-id="1d841-106">[in] Bit düzeyinde bileşimini [notıfy_fılter](../../../../docs/framework/unmanaged-api/diagnostics/notify-filter-enumeration.md) geri aramalar için hata ayıklayıcı API tanımlamak numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="1d841-106">[in] A bitwise combination of the [NOTIFY_FILTER](../../../../docs/framework/unmanaged-api/diagnostics/notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="1d841-107">[in] Bir işaretçi bir [USER_THREAD](../../../../docs/framework/unmanaged-api/diagnostics/user-thread-structure.md) API hata ayıklayıcı için iş parçacığı tanımlayan yapısı.</span><span class="sxs-lookup"><span data-stu-id="1d841-107">[in] A pointer to a [USER_THREAD](../../../../docs/framework/unmanaged-api/diagnostics/user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d841-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1d841-108">Return Value</span></span>  
 <span data-ttu-id="1d841-109">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="1d841-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d841-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d841-110">Requirements</span></span>  
 <span data-ttu-id="1d841-111">**Başlık:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="1d841-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d841-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d841-112">See Also</span></span>  
 [<span data-ttu-id="1d841-113">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d841-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="1d841-114">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d841-114">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [<span data-ttu-id="1d841-115">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d841-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
