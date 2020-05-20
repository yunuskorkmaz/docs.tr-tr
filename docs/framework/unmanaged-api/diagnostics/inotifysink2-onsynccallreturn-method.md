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
ms.openlocfilehash: ff1dabcfc366607639cd98be4392f8dd59dc83a1
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442013"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="1d760-102">INotifySink2::OnSyncCallReturn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d760-102">INotifySink2::OnSyncCallReturn Method</span></span>
<span data-ttu-id="1d760-103">Bir çağrı geri döndüğünde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1d760-103">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d760-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1d760-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d760-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1d760-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="1d760-106">'ndaki Döndürülen çağrının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="1d760-106">[in] ID of the call being returned from.</span></span> <span data-ttu-id="1d760-107">Bkz. [CALL_ID yapısı](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="1d760-107">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="1d760-108">'ndaki Çağrı arabelleği.</span><span class="sxs-lookup"><span data-stu-id="1d760-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="1d760-109">'ndaki Çağrı arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="1d760-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d760-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1d760-110">Return Value</span></span>  
 <span data-ttu-id="1d760-111">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="1d760-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d760-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d760-112">Requirements</span></span>  
 <span data-ttu-id="1d760-113">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="1d760-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d760-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d760-114">See also</span></span>

- [<span data-ttu-id="1d760-115">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d760-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="1d760-116">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d760-116">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="1d760-117">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d760-117">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
