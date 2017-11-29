---
title: "INotifyConnection2::RegisterNotifySource Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifyConnection2.RegisterNotifySource
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 370f19d9fd1cbc268d43b9970b0cf27290796562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="47f46-102">INotifyConnection2::RegisterNotifySource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47f46-102">INotifyConnection2::RegisterNotifySource Method</span></span>
<span data-ttu-id="47f46-103">Belirtilen bildirim kaynağı yükler.</span><span class="sxs-lookup"><span data-stu-id="47f46-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47f46-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47f46-104">Syntax</span></span>  
  
```  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47f46-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47f46-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="47f46-106">[in] Bildirim kaynağı olarak kullanılacak nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="47f46-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="47f46-107">[out] Bildirim havuzu olarak kullanılacak nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="47f46-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47f46-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="47f46-108">Return Value</span></span>  
 <span data-ttu-id="47f46-109">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="47f46-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47f46-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47f46-110">Requirements</span></span>  
 <span data-ttu-id="47f46-111">**Başlık:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="47f46-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47f46-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47f46-112">See Also</span></span>  
 [<span data-ttu-id="47f46-113">Inotifyconnection2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="47f46-113">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [<span data-ttu-id="47f46-114">Inotifysource2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="47f46-114">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="47f46-115">Inotifysink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="47f46-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="47f46-116">UnregisterNotifySource yöntemi</span><span class="sxs-lookup"><span data-stu-id="47f46-116">UnregisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-unregisternotifysource-method.md)
