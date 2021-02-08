---
description: ': INotifySource2:: SetNotifyFilter yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 2aaf2a5253f8a9acb67c4b538f109a7a62559d12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800233"
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="f068d-103">INotifySource2::SetNotifyFilter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f068d-103">INotifySource2::SetNotifyFilter Method</span></span>

<span data-ttu-id="f068d-104">Bu kaynakla kullanılmak üzere bir bildirim filtresi atar.</span><span class="sxs-lookup"><span data-stu-id="f068d-104">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f068d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f068d-105">Syntax</span></span>  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f068d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f068d-106">Parameters</span></span>  

 `in_NotifyFilter`  
 <span data-ttu-id="f068d-107">'ndaki Hata ayıklayıcı API 'SI için geri çağırmaları tanımlayan [NOTIFY_FILTER](notify-filter-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="f068d-107">[in] A bitwise combination of the [NOTIFY_FILTER](notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="f068d-108">'ndaki Hata ayıklayıcı API 'SI için iş parçacıklarını tanımlayan [USER_THREAD](user-thread-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f068d-108">[in] A pointer to a [USER_THREAD](user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f068d-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f068d-109">Return Value</span></span>  

 <span data-ttu-id="f068d-110">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="f068d-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f068d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f068d-111">Requirements</span></span>  

 <span data-ttu-id="f068d-112">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="f068d-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f068d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f068d-113">See also</span></span>

- [<span data-ttu-id="f068d-114">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f068d-114">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="f068d-115">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f068d-115">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="f068d-116">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f068d-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
