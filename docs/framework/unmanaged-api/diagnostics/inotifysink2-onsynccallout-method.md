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
ms.openlocfilehash: 00f6032f41caf54d7366de30a449f1ae76e8bbd0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719989"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="5509c-102">INotifySink2::OnSyncCallOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5509c-102">INotifySink2::OnSyncCallOut Method</span></span>

<span data-ttu-id="5509c-103">Bir çağrı çıkış olduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5509c-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5509c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5509c-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5509c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5509c-105">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="5509c-106">'ndaki Giden çağrının KIMLIĞI. Bkz. [CALL_ID yapısı](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="5509c-106">[in] ID of the call that is out. See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="5509c-107">dışı Çağrı arabelleği.</span><span class="sxs-lookup"><span data-stu-id="5509c-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="5509c-108">dışı Çağrı arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="5509c-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5509c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5509c-109">Return Value</span></span>  

 <span data-ttu-id="5509c-110">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="5509c-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5509c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5509c-111">Requirements</span></span>  

 <span data-ttu-id="5509c-112">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="5509c-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5509c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5509c-113">See also</span></span>

- [<span data-ttu-id="5509c-114">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5509c-114">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="5509c-115">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5509c-115">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="5509c-116">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5509c-116">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
