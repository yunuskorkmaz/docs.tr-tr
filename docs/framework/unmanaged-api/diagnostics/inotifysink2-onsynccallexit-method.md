---
description: 'Şu konuda daha fazla bilgi edinin: INotifySink2:: OnSyncCallExit Yöntemi'
title: INotifySink2::OnSyncCallExit Yöntemi
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallExit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type:
- apiref
ms.openlocfilehash: 2de55c3b7956576049e4ad65b2cb6fbc69fa84af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800272"
---
# <a name="inotifysink2onsynccallexit-method"></a><span data-ttu-id="680d7-103">INotifySink2::OnSyncCallExit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="680d7-103">INotifySink2::OnSyncCallExit Method</span></span>

<span data-ttu-id="680d7-104">Bir çağrıdan çıkarken çağrılır.</span><span class="sxs-lookup"><span data-stu-id="680d7-104">Gets invoked when exiting a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="680d7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="680d7-105">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="680d7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="680d7-106">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="680d7-107">'ndaki Çıkılmakta olan çağrının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="680d7-107">[in] ID of the call being exited.</span></span> <span data-ttu-id="680d7-108">Bkz. [CALL_ID yapısı](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="680d7-108">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="680d7-109">dışı Çağrı arabelleği.</span><span class="sxs-lookup"><span data-stu-id="680d7-109">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="680d7-110">dışı Çağrı arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="680d7-110">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="680d7-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="680d7-111">Return Value</span></span>  

 <span data-ttu-id="680d7-112">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="680d7-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="680d7-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="680d7-113">Requirements</span></span>  

 <span data-ttu-id="680d7-114">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="680d7-114">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="680d7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="680d7-115">See also</span></span>

- [<span data-ttu-id="680d7-116">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="680d7-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="680d7-117">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="680d7-117">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="680d7-118">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="680d7-118">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
