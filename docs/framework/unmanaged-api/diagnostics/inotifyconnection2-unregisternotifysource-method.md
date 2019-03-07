---
title: INotifyConnection2::UnregisterNotifySource Yöntemi
ms.date: 03/30/2017
api_name:
- INotifyConnection2.UnregisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b7125ad38bcec773fa2afa8eca09c1d56d90591
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475781"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="607a6-102">INotifyConnection2::UnregisterNotifySource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="607a6-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="607a6-103">Belirtilen bildirim kaynak nesnesi bağlantıyı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="607a6-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="607a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="607a6-104">Syntax</span></span>  
  
```  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="607a6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="607a6-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="607a6-106">[in] Sona erdirilecek bildirim nesnesi.</span><span class="sxs-lookup"><span data-stu-id="607a6-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="607a6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="607a6-107">Return Value</span></span>  
 <span data-ttu-id="607a6-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="607a6-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="607a6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="607a6-109">Requirements</span></span>  
 <span data-ttu-id="607a6-110">**Üst bilgi:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="607a6-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="607a6-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="607a6-111">See also</span></span>
- [<span data-ttu-id="607a6-112">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="607a6-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="607a6-113">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="607a6-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="607a6-114">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="607a6-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="607a6-115">RegisterNotifySource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="607a6-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
