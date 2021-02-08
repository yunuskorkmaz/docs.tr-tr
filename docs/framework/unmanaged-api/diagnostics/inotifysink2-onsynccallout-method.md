---
description: 'Daha fazla bilgi edinin: INotifySink2:: Onsyncbelirtme yöntemi'
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
ms.openlocfilehash: 03028b138a7d95c618ae20530f66aa692d314cab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800246"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="77ff4-103">INotifySink2::OnSyncCallOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77ff4-103">INotifySink2::OnSyncCallOut Method</span></span>

<span data-ttu-id="77ff4-104">Bir çağrı çıkış olduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="77ff4-104">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77ff4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77ff4-105">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77ff4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="77ff4-106">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="77ff4-107">'ndaki Giden çağrının KIMLIĞI. Bkz. [CALL_ID yapısı](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="77ff4-107">[in] ID of the call that is out. See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="77ff4-108">dışı Çağrı arabelleği.</span><span class="sxs-lookup"><span data-stu-id="77ff4-108">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="77ff4-109">dışı Çağrı arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="77ff4-109">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77ff4-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="77ff4-110">Return Value</span></span>  

 <span data-ttu-id="77ff4-111">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="77ff4-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77ff4-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77ff4-112">Requirements</span></span>  

 <span data-ttu-id="77ff4-113">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="77ff4-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77ff4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77ff4-114">See also</span></span>

- [<span data-ttu-id="77ff4-115">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77ff4-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="77ff4-116">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77ff4-116">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="77ff4-117">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77ff4-117">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
