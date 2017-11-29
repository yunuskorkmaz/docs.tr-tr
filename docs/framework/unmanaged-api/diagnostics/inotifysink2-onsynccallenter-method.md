---
title: "INotifySink2::OnSyncCallEnter Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifySink2.OnSyncCallEnter
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifySink2::OnSyncCallEnter
helpviewer_keywords:
- INotifySink2::OnSyncCallEnter method [.NET Framework debugging]
- OnSyncCallEnter method [.NET Framework debugging]
ms.assetid: e33265be-c25d-4145-ad02-c3e89d6f26c1
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 99ffca48e33baed3a1e5700090194c1ef8c6f357
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="inotifysink2onsynccallenter-method"></a><span data-ttu-id="c3ab3-102">INotifySink2::OnSyncCallEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3ab3-102">INotifySink2::OnSyncCallEnter Method</span></span>
<span data-ttu-id="c3ab3-103">Bir çağrı girerken çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c3ab3-103">Gets invoked when entering a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3ab3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3ab3-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3ab3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3ab3-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="c3ab3-106">[in] Girilen çağrı kimliği.</span><span class="sxs-lookup"><span data-stu-id="c3ab3-106">[in] ID of the call being entered.</span></span> <span data-ttu-id="c3ab3-107">Bkz: [call_ıd yapısı](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="c3ab3-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="c3ab3-108">[in] Arabellek çağırın.</span><span class="sxs-lookup"><span data-stu-id="c3ab3-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="c3ab3-109">[in] Çağrı arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="c3ab3-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3ab3-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c3ab3-110">Return Value</span></span>  
 <span data-ttu-id="c3ab3-111">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="c3ab3-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3ab3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3ab3-112">Requirements</span></span>  
 <span data-ttu-id="c3ab3-113">**Başlık:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="c3ab3-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ab3-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c3ab3-114">See Also</span></span>  
 [<span data-ttu-id="c3ab3-115">Inotifysink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3ab3-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="c3ab3-116">Inotifysource2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3ab3-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="c3ab3-117">Inotifyconnection2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3ab3-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
