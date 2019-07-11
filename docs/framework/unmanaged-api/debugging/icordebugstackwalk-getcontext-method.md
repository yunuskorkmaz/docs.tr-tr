---
title: ICorDebugStackWalk::GetContext Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f453e950a79b0f929ec8f813cc13eb2e01ab8c87
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760932"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="94431-102">ICorDebugStackWalk::GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94431-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="94431-103">Geçerli kare bağlamını döndürür [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="94431-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94431-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94431-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94431-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94431-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="94431-106">[in] İstenen içeriği (WinNT.h içinde tanımlanmıştır) bağlam arabellek belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="94431-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="94431-107">[in] Ayrılmış bağlam arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="94431-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="94431-108">[out] Bağlam gerçek boyutu.</span><span class="sxs-lookup"><span data-stu-id="94431-108">[out] The actual size of the context.</span></span> <span data-ttu-id="94431-109">Bu değer, ya da bağlam arabellek boyutu eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94431-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="94431-110">[out] İçerik arabelleği.</span><span class="sxs-lookup"><span data-stu-id="94431-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94431-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="94431-111">Return Value</span></span>  
 <span data-ttu-id="94431-112">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="94431-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="94431-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94431-113">HRESULT</span></span>|<span data-ttu-id="94431-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94431-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94431-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="94431-115">S_OK</span></span>|<span data-ttu-id="94431-116">Geçerli çerçevenin içeriği başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="94431-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="94431-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="94431-117">E_FAIL</span></span>|<span data-ttu-id="94431-118">Bağlam döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="94431-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="94431-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="94431-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="94431-120">Bağlam arabellek çok küçük.</span><span class="sxs-lookup"><span data-stu-id="94431-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="94431-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="94431-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="94431-122">Çerçeve işaretçisini yığının sonuna bulunur. Bu nedenle, hiçbir ek çerçeveler erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="94431-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="94431-123">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="94431-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94431-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94431-124">Remarks</span></span>  
 <span data-ttu-id="94431-125">Geriye doğru izleme yalnızca bir alt yazmaçların geçici olmayan kayıtlar gibi geri yükler için bağlam aramanın zaman tam olarak kayıt durumu eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="94431-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94431-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94431-126">Requirements</span></span>  
 <span data-ttu-id="94431-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94431-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94431-128">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94431-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94431-129">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94431-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94431-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94431-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94431-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94431-131">See also</span></span>

- [<span data-ttu-id="94431-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="94431-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="94431-133">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="94431-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
