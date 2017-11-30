---
title: "INotifySink2::OnSyncCallExit Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifySink2.OnSyncCallExit
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8034717826316fe8ae4679c19e5002ca2c22c6fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="inotifysink2onsynccallexit-method"></a><span data-ttu-id="52c07-102">INotifySink2::OnSyncCallExit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52c07-102">INotifySink2::OnSyncCallExit Method</span></span>
<span data-ttu-id="52c07-103">Bir çağrı çıkarken çağrılır.</span><span class="sxs-lookup"><span data-stu-id="52c07-103">Gets invoked when exiting a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52c07-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52c07-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52c07-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52c07-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="52c07-106">[in] Çıktı çağrısı kimliği.</span><span class="sxs-lookup"><span data-stu-id="52c07-106">[in] ID of the call being exited.</span></span> <span data-ttu-id="52c07-107">Bkz: [call_ıd yapısı](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="52c07-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="52c07-108">[out] Arabellek çağırın.</span><span class="sxs-lookup"><span data-stu-id="52c07-108">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="52c07-109">[out] Çağrı arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="52c07-109">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52c07-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="52c07-110">Return Value</span></span>  
 <span data-ttu-id="52c07-111">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="52c07-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52c07-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52c07-112">Requirements</span></span>  
 <span data-ttu-id="52c07-113">**Başlık:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="52c07-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c07-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52c07-114">See Also</span></span>  
 [<span data-ttu-id="52c07-115">Inotifysink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="52c07-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="52c07-116">Inotifysource2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="52c07-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="52c07-117">Inotifyconnection2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="52c07-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
