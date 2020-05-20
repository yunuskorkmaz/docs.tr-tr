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
ms.openlocfilehash: 85f00698f42f120b209cca14f293a58ae4c65f6f
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442039"
---
# <a name="inotifysink2onsynccallenter-method"></a><span data-ttu-id="34a27-102">INotifySink2::OnSyncCallEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34a27-102">INotifySink2::OnSyncCallEnter Method</span></span>
<span data-ttu-id="34a27-103">Bir çağrı girilirken çağrılır.</span><span class="sxs-lookup"><span data-stu-id="34a27-103">Gets invoked when entering a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34a27-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="34a27-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34a27-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34a27-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="34a27-106">'ndaki Girilen çağrının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="34a27-106">[in] ID of the call being entered.</span></span> <span data-ttu-id="34a27-107">Bkz. [CALL_ID yapısı](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="34a27-107">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="34a27-108">'ndaki Çağrı arabelleği.</span><span class="sxs-lookup"><span data-stu-id="34a27-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="34a27-109">'ndaki Çağrı arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="34a27-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34a27-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="34a27-110">Return Value</span></span>  
 <span data-ttu-id="34a27-111">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="34a27-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34a27-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34a27-112">Requirements</span></span>  
 <span data-ttu-id="34a27-113">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="34a27-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34a27-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34a27-114">See also</span></span>

- [<span data-ttu-id="34a27-115">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34a27-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="34a27-116">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34a27-116">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="34a27-117">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34a27-117">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
