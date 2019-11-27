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
ms.openlocfilehash: cf399d0c7dec7528f02988ddfe6ca5c0b1f0c4c3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440990"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="cc7b2-102">INotifyConnection2::UnregisterNotifySource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc7b2-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="cc7b2-103">Belirtilen bir bildirim kaynağı nesnesini bağlantıdan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cc7b2-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc7b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc7b2-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc7b2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc7b2-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="cc7b2-106">'ndaki Kayıt kaldırılacak bildirim nesnesi.</span><span class="sxs-lookup"><span data-stu-id="cc7b2-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc7b2-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cc7b2-107">Return Value</span></span>  
 <span data-ttu-id="cc7b2-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="cc7b2-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc7b2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc7b2-109">Requirements</span></span>  
 <span data-ttu-id="cc7b2-110">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="cc7b2-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc7b2-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc7b2-111">See also</span></span>

- [<span data-ttu-id="cc7b2-112">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc7b2-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="cc7b2-113">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc7b2-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="cc7b2-114">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc7b2-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="cc7b2-115">RegisterNotifySource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc7b2-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
