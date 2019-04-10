---
title: INotifySink2::OnSyncCallEnter Yöntemi
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallEnter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallEnter
helpviewer_keywords:
- INotifySink2::OnSyncCallEnter method [.NET Framework debugging]
- OnSyncCallEnter method [.NET Framework debugging]
ms.assetid: e33265be-c25d-4145-ad02-c3e89d6f26c1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 78aaa5d8031e7b554eee2a147d9940ff8d7f7e02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201903"
---
# <a name="inotifysink2onsynccallenter-method"></a><span data-ttu-id="028e7-102">INotifySink2::OnSyncCallEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="028e7-102">INotifySink2::OnSyncCallEnter Method</span></span>
<span data-ttu-id="028e7-103">Bir çağrı girerken çağrılır.</span><span class="sxs-lookup"><span data-stu-id="028e7-103">Gets invoked when entering a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="028e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="028e7-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="028e7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="028e7-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="028e7-106">[in] Girilen çağrı kimliği.</span><span class="sxs-lookup"><span data-stu-id="028e7-106">[in] ID of the call being entered.</span></span> <span data-ttu-id="028e7-107">Bkz: [call_ıd yapısı](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="028e7-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="028e7-108">[in] Arabellek çağırın.</span><span class="sxs-lookup"><span data-stu-id="028e7-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="028e7-109">[in] Çağrı arabelleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="028e7-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="028e7-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="028e7-110">Return Value</span></span>  
 <span data-ttu-id="028e7-111">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="028e7-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="028e7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="028e7-112">Requirements</span></span>  
 <span data-ttu-id="028e7-113">**Üst bilgi:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="028e7-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="028e7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="028e7-114">See also</span></span>

- [<span data-ttu-id="028e7-115">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="028e7-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="028e7-116">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="028e7-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="028e7-117">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="028e7-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
