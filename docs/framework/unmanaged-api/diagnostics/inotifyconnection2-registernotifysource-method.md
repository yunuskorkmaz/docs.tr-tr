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
ms.openlocfilehash: b7fa777466e2c7edd7b3110dd91e776785c63c58
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442078"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="b27c6-102">INotifyConnection2::RegisterNotifySource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b27c6-102">INotifyConnection2::RegisterNotifySource Method</span></span>
<span data-ttu-id="b27c6-103">Belirtilen bir bildirim kaynağını yükleme.</span><span class="sxs-lookup"><span data-stu-id="b27c6-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b27c6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b27c6-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b27c6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b27c6-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="b27c6-106">'ndaki Bildirim kaynağı olarak kullanılacak nesneyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b27c6-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="b27c6-107">dışı Bildirim havuzu olarak kullanılacak nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="b27c6-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b27c6-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b27c6-108">Return Value</span></span>  
 <span data-ttu-id="b27c6-109">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="b27c6-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b27c6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b27c6-110">Requirements</span></span>  
 <span data-ttu-id="b27c6-111">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="b27c6-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b27c6-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b27c6-112">See also</span></span>

- [<span data-ttu-id="b27c6-113">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b27c6-113">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="b27c6-114">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b27c6-114">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="b27c6-115">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b27c6-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="b27c6-116">UnregisterNotifySource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b27c6-116">UnregisterNotifySource Method</span></span>](inotifyconnection2-unregisternotifysource-method.md)
