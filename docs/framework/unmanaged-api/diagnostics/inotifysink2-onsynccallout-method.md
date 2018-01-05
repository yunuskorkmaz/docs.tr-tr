---
title: "INotifySink2::OnSyncCallOut Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifySink2.OnSyncCallOut
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 484027fe0ab8e5e416059678d2603080ed730be3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="b7b0b-102">INotifySink2::OnSyncCallOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7b0b-102">INotifySink2::OnSyncCallOut Method</span></span>
<span data-ttu-id="b7b0b-103">Bir çağrı çıkışı olduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b7b0b-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7b0b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7b0b-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7b0b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7b0b-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="b7b0b-106">[in] Out olduğu çağrı kimliği. Bkz: [call_ıd yapısı](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="b7b0b-106">[in] ID of the call that is out. See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="b7b0b-107">[out] Arabellek çağırın.</span><span class="sxs-lookup"><span data-stu-id="b7b0b-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="b7b0b-108">[out] Çağrı arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b7b0b-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7b0b-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b7b0b-109">Return Value</span></span>  
 <span data-ttu-id="b7b0b-110">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="b7b0b-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7b0b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7b0b-111">Requirements</span></span>  
 <span data-ttu-id="b7b0b-112">**Başlık:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="b7b0b-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b0b-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b7b0b-113">See Also</span></span>  
 [<span data-ttu-id="b7b0b-114">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7b0b-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="b7b0b-115">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7b0b-115">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="b7b0b-116">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7b0b-116">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
