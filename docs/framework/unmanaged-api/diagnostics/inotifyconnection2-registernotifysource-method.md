---
description: 'Daha fazla bilgi edinin: INotifyConnection2:: RegisterNotifySource Yöntemi'
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
ms.openlocfilehash: 97aacf7f2005a1e9f21acebd6c5f5ed65867b245
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800324"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="6b2a0-103">INotifyConnection2::RegisterNotifySource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b2a0-103">INotifyConnection2::RegisterNotifySource Method</span></span>

<span data-ttu-id="6b2a0-104">Belirtilen bir bildirim kaynağını yükleme.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-104">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b2a0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b2a0-105">Syntax</span></span>  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b2a0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6b2a0-106">Parameters</span></span>  

 `in_pNotifySource`  
 <span data-ttu-id="6b2a0-107">'ndaki Bildirim kaynağı olarak kullanılacak nesneyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-107">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="6b2a0-108">dışı Bildirim havuzu olarak kullanılacak nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-108">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b2a0-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6b2a0-109">Return Value</span></span>  

 <span data-ttu-id="6b2a0-110">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b2a0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b2a0-111">Requirements</span></span>  

 <span data-ttu-id="6b2a0-112">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="6b2a0-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b2a0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-113">See also</span></span>

- [<span data-ttu-id="6b2a0-114">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b2a0-114">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="6b2a0-115">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b2a0-115">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="6b2a0-116">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b2a0-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="6b2a0-117">UnregisterNotifySource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b2a0-117">UnregisterNotifySource Method</span></span>](inotifyconnection2-unregisternotifysource-method.md)
