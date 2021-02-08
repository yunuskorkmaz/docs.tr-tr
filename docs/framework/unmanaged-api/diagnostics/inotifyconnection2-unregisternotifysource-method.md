---
description: ': INotifyConnection2:: UnregisterNotifySource yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d3b82665375f54d33b6a5581241788d828060a83
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800311"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="9f1a6-103">INotifyConnection2::UnregisterNotifySource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f1a6-103">INotifyConnection2::UnregisterNotifySource Method</span></span>

<span data-ttu-id="9f1a6-104">Belirtilen bir bildirim kaynağı nesnesini bağlantıdan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9f1a6-104">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f1a6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f1a6-105">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f1a6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f1a6-106">Parameters</span></span>  

 `in_pNotifySource`  
 <span data-ttu-id="9f1a6-107">'ndaki Kayıt kaldırılacak bildirim nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9f1a6-107">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f1a6-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9f1a6-108">Return Value</span></span>  

 <span data-ttu-id="9f1a6-109">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="9f1a6-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f1a6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f1a6-110">Requirements</span></span>  

 <span data-ttu-id="9f1a6-111">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="9f1a6-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f1a6-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f1a6-112">See also</span></span>

- [<span data-ttu-id="9f1a6-113">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f1a6-113">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="9f1a6-114">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f1a6-114">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="9f1a6-115">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f1a6-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="9f1a6-116">RegisterNotifySource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f1a6-116">RegisterNotifySource Method</span></span>](inotifyconnection2-registernotifysource-method.md)
