---
title: INotifyConnection2::RegisterNotifySource Yöntemi
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9dac5ae2f0f77c7b6d2dbd7f908f3552823735b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940432"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="f161f-102">INotifyConnection2::RegisterNotifySource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f161f-102">INotifyConnection2::RegisterNotifySource Method</span></span>
<span data-ttu-id="f161f-103">Belirtilen bildirim kaynak yükler.</span><span class="sxs-lookup"><span data-stu-id="f161f-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f161f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f161f-104">Syntax</span></span>  
  
```  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f161f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f161f-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="f161f-106">[in] Bildirim kaynağı olarak kullanılacak nesneyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f161f-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="f161f-107">[out] Bildirim havuz olarak kullanılacak nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="f161f-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f161f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f161f-108">Return Value</span></span>  
 <span data-ttu-id="f161f-109">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="f161f-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f161f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f161f-110">Requirements</span></span>  
 <span data-ttu-id="f161f-111">**Üst bilgi:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="f161f-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f161f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f161f-112">See also</span></span>

- [<span data-ttu-id="f161f-113">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f161f-113">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="f161f-114">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f161f-114">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="f161f-115">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f161f-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="f161f-116">UnregisterNotifySource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f161f-116">UnregisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-unregisternotifysource-method.md)
