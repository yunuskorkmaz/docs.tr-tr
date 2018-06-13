---
title: INotifySink2::OnSyncCallReturn Yöntemi
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallReturn
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ebfa886e85cd72c4ea7d088ef345bc9968dec18f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426013"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="866e1-102">INotifySink2::OnSyncCallReturn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="866e1-102">INotifySink2::OnSyncCallReturn Method</span></span>
<span data-ttu-id="866e1-103">Bir çağrısı döndürüldüğünde çağrılan.</span><span class="sxs-lookup"><span data-stu-id="866e1-103">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="866e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="866e1-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="866e1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="866e1-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="866e1-106">[in] Sunucudan döndürülen arama kimliği.</span><span class="sxs-lookup"><span data-stu-id="866e1-106">[in] ID of the call being returned from.</span></span> <span data-ttu-id="866e1-107">Bkz: [call_ıd yapısı](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="866e1-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="866e1-108">[in] Arabellek çağırın.</span><span class="sxs-lookup"><span data-stu-id="866e1-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="866e1-109">[in] Çağrı arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="866e1-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="866e1-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="866e1-110">Return Value</span></span>  
 <span data-ttu-id="866e1-111">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="866e1-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="866e1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="866e1-112">Requirements</span></span>  
 <span data-ttu-id="866e1-113">**Başlık:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="866e1-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="866e1-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="866e1-114">See Also</span></span>  
 [<span data-ttu-id="866e1-115">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="866e1-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="866e1-116">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="866e1-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="866e1-117">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="866e1-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
