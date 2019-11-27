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
ms.openlocfilehash: d2d90d33ce7a8135f40a0fb4039a2418dd1987ac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435974"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="a09f0-102">INotifySink2::OnSyncCallReturn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a09f0-102">INotifySink2::OnSyncCallReturn Method</span></span>
<span data-ttu-id="a09f0-103">Bir çağrı geri döndüğünde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a09f0-103">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a09f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a09f0-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a09f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a09f0-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="a09f0-106">'ndaki Döndürülen çağrının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a09f0-106">[in] ID of the call being returned from.</span></span> <span data-ttu-id="a09f0-107">Bkz. [CALL_ID yapısı](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="a09f0-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="a09f0-108">'ndaki Çağrı arabelleği.</span><span class="sxs-lookup"><span data-stu-id="a09f0-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="a09f0-109">'ndaki Çağrı arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="a09f0-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a09f0-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a09f0-110">Return Value</span></span>  
 <span data-ttu-id="a09f0-111">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="a09f0-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a09f0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a09f0-112">Requirements</span></span>  
 <span data-ttu-id="a09f0-113">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="a09f0-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a09f0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a09f0-114">See also</span></span>

- [<span data-ttu-id="a09f0-115">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a09f0-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="a09f0-116">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a09f0-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="a09f0-117">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a09f0-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
