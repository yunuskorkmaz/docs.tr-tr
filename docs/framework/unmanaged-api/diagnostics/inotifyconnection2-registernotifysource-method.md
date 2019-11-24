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
ms.openlocfilehash: 76514cfbd2e533f04c5139dbaef4429c12463106
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445466"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="feb67-102">INotifyConnection2::RegisterNotifySource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="feb67-102">INotifyConnection2::RegisterNotifySource Method</span></span>
<span data-ttu-id="feb67-103">Installs a specified notification source.</span><span class="sxs-lookup"><span data-stu-id="feb67-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feb67-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="feb67-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="feb67-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="feb67-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="feb67-106">[in] Specifies the object to be used as the notification source.</span><span class="sxs-lookup"><span data-stu-id="feb67-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="feb67-107">[out] Receives the object to be used as the notification sink.</span><span class="sxs-lookup"><span data-stu-id="feb67-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="feb67-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="feb67-108">Return Value</span></span>  
 <span data-ttu-id="feb67-109">S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="feb67-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feb67-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="feb67-110">Requirements</span></span>  
 <span data-ttu-id="feb67-111">**Header:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="feb67-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feb67-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="feb67-112">See also</span></span>

- [<span data-ttu-id="feb67-113">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="feb67-113">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="feb67-114">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="feb67-114">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="feb67-115">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="feb67-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="feb67-116">UnregisterNotifySource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="feb67-116">UnregisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-unregisternotifysource-method.md)
