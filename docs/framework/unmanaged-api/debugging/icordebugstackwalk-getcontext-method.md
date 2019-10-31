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
ms.openlocfilehash: 700e0af05828b9fe0a50c1aac114e840adc276b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131845"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="52de1-102">ICorDebugStackWalk::GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52de1-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="52de1-103">[Icordebugstackyürüme](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesnesindeki geçerli karenin bağlamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="52de1-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52de1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52de1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52de1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52de1-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="52de1-106">'ndaki Bağlam arabelleğinin istenen içeriğini belirten bayraklar (WinNT. h içinde tanımlanmıştır).</span><span class="sxs-lookup"><span data-stu-id="52de1-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="52de1-107">'ndaki Bağlam arabelleğinin ayrılan boyutu.</span><span class="sxs-lookup"><span data-stu-id="52de1-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="52de1-108">dışı Bağlamın gerçek boyutu.</span><span class="sxs-lookup"><span data-stu-id="52de1-108">[out] The actual size of the context.</span></span> <span data-ttu-id="52de1-109">Bu değer, bağlam arabelleğinin boyutundan küçük veya buna eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="52de1-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="52de1-110">dışı Bağlam arabelleği.</span><span class="sxs-lookup"><span data-stu-id="52de1-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52de1-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="52de1-111">Return Value</span></span>  
 <span data-ttu-id="52de1-112">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="52de1-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="52de1-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52de1-113">HRESULT</span></span>|<span data-ttu-id="52de1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52de1-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52de1-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="52de1-115">S_OK</span></span>|<span data-ttu-id="52de1-116">Geçerli çerçevenin bağlamı başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="52de1-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="52de1-117">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="52de1-117">E_FAIL</span></span>|<span data-ttu-id="52de1-118">Bağlam döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="52de1-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="52de1-119">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="52de1-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="52de1-120">Bağlam arabelleği çok küçük.</span><span class="sxs-lookup"><span data-stu-id="52de1-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="52de1-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="52de1-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="52de1-122">Çerçeve işaretçisi zaten yığının sonunda. Bu nedenle, ek çerçevelere erişilemez.</span><span class="sxs-lookup"><span data-stu-id="52de1-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="52de1-123">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="52de1-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52de1-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52de1-124">Remarks</span></span>  
 <span data-ttu-id="52de1-125">Geriye doğru kaldırma, geçici olmayan Yazmaçları gibi yazmaçların yalnızca bir alt kümesini geri yüklediği için, bağlam çağrı sırasında kayıt durumuyla tam olarak eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="52de1-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52de1-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52de1-126">Requirements</span></span>  
 <span data-ttu-id="52de1-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52de1-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52de1-128">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="52de1-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52de1-129">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="52de1-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52de1-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52de1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52de1-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52de1-131">See also</span></span>

- [<span data-ttu-id="52de1-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="52de1-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="52de1-133">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="52de1-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
