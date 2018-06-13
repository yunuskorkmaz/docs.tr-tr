---
title: INotifySink2::OnSyncCallOut Yöntemi
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a38c35f0acd47c9183c043e1c436413a309b138
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426081"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="97401-102">INotifySink2::OnSyncCallOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97401-102">INotifySink2::OnSyncCallOut Method</span></span>
<span data-ttu-id="97401-103">Bir çağrı çıkışı olduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="97401-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97401-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97401-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97401-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97401-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="97401-106">[in] Out olduğu çağrı kimliği. Bkz: [call_ıd yapısı](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="97401-106">[in] ID of the call that is out. See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="97401-107">[out] Arabellek çağırın.</span><span class="sxs-lookup"><span data-stu-id="97401-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="97401-108">[out] Çağrı arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="97401-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97401-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="97401-109">Return Value</span></span>  
 <span data-ttu-id="97401-110">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="97401-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97401-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97401-111">Requirements</span></span>  
 <span data-ttu-id="97401-112">**Başlık:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="97401-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97401-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97401-113">See Also</span></span>  
 [<span data-ttu-id="97401-114">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97401-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="97401-115">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97401-115">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="97401-116">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97401-116">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
