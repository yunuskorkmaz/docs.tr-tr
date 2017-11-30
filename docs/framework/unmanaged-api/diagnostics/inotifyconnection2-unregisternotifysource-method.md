---
title: "INotifyConnection2::UnregisterNotifySource Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifyConnection2.UnregisterNotifySource
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 063a146d31031f0cb14e00278819e8cd874f98c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="69bdb-102">INotifyConnection2::UnregisterNotifySource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69bdb-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="69bdb-103">Belirtilen bildirim kaynak nesne bağlantıyı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="69bdb-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69bdb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69bdb-104">Syntax</span></span>  
  
```  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69bdb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69bdb-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="69bdb-106">[in] Sona erdirilecek bildirim nesnesi.</span><span class="sxs-lookup"><span data-stu-id="69bdb-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69bdb-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="69bdb-107">Return Value</span></span>  
 <span data-ttu-id="69bdb-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="69bdb-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69bdb-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69bdb-109">Requirements</span></span>  
 <span data-ttu-id="69bdb-110">**Başlık:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="69bdb-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69bdb-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69bdb-111">See Also</span></span>  
 [<span data-ttu-id="69bdb-112">Inotifyconnection2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="69bdb-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [<span data-ttu-id="69bdb-113">Inotifysource2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="69bdb-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="69bdb-114">Inotifysink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="69bdb-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="69bdb-115">RegisterNotifySource yöntemi</span><span class="sxs-lookup"><span data-stu-id="69bdb-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
