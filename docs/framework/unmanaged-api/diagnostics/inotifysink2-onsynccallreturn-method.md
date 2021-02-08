---
description: 'Şu konuda daha fazla bilgi edinin: INotifySink2:: OnSyncCallReturn yöntemi'
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
ms.openlocfilehash: 01518de4e5a9e1374edddadb3c49f16e8fe679a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800259"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="fd21e-103">INotifySink2::OnSyncCallReturn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd21e-103">INotifySink2::OnSyncCallReturn Method</span></span>

<span data-ttu-id="fd21e-104">Bir çağrı geri döndüğünde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fd21e-104">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd21e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd21e-105">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd21e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd21e-106">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="fd21e-107">'ndaki Döndürülen çağrının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="fd21e-107">[in] ID of the call being returned from.</span></span> <span data-ttu-id="fd21e-108">Bkz. [CALL_ID yapısı](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="fd21e-108">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="fd21e-109">'ndaki Çağrı arabelleği.</span><span class="sxs-lookup"><span data-stu-id="fd21e-109">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="fd21e-110">'ndaki Çağrı arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="fd21e-110">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd21e-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fd21e-111">Return Value</span></span>  

 <span data-ttu-id="fd21e-112">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="fd21e-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd21e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd21e-113">Requirements</span></span>  

 <span data-ttu-id="fd21e-114">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="fd21e-114">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd21e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd21e-115">See also</span></span>

- [<span data-ttu-id="fd21e-116">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd21e-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="fd21e-117">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd21e-117">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="fd21e-118">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd21e-118">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
