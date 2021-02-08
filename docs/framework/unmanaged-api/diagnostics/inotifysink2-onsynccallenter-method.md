---
description: 'Şu konuda daha fazla bilgi edinin: INotifySink2:: OnSyncCallEnter yöntemi'
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
ms.openlocfilehash: e7537b16ec8ea8d92ad92498c1bfdac5a9de6475
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800285"
---
# <a name="inotifysink2onsynccallenter-method"></a><span data-ttu-id="ebdc0-103">INotifySink2::OnSyncCallEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebdc0-103">INotifySink2::OnSyncCallEnter Method</span></span>

<span data-ttu-id="ebdc0-104">Bir çağrı girilirken çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ebdc0-104">Gets invoked when entering a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebdc0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ebdc0-105">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebdc0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ebdc0-106">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="ebdc0-107">'ndaki Girilen çağrının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="ebdc0-107">[in] ID of the call being entered.</span></span> <span data-ttu-id="ebdc0-108">Bkz. [CALL_ID yapısı](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="ebdc0-108">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="ebdc0-109">'ndaki Çağrı arabelleği.</span><span class="sxs-lookup"><span data-stu-id="ebdc0-109">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="ebdc0-110">'ndaki Çağrı arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ebdc0-110">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebdc0-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ebdc0-111">Return Value</span></span>  

 <span data-ttu-id="ebdc0-112">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="ebdc0-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebdc0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebdc0-113">Requirements</span></span>  

 <span data-ttu-id="ebdc0-114">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="ebdc0-114">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebdc0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebdc0-115">See also</span></span>

- [<span data-ttu-id="ebdc0-116">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebdc0-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="ebdc0-117">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebdc0-117">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="ebdc0-118">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebdc0-118">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
