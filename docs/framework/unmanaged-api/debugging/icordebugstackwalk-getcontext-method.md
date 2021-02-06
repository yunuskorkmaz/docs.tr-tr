---
description: ': Icordebugstackizlenecek yol:: GetContext yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 30beefaa1e0e2e4c5043cae7213658ac24e8a1b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649617"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="6c0eb-103">ICorDebugStackWalk::GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c0eb-103">ICorDebugStackWalk::GetContext Method</span></span>

<span data-ttu-id="6c0eb-104">[Icordebugstackyürüme](icordebugstackwalk-interface.md) nesnesindeki geçerli karenin bağlamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c0eb-104">Returns the context for the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c0eb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c0eb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c0eb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c0eb-106">Parameters</span></span>  

 `contextFlags`  
 <span data-ttu-id="6c0eb-107">'ndaki Bağlam arabelleğinin istenen içeriğini belirten bayraklar (WinNT. h içinde tanımlanmıştır).</span><span class="sxs-lookup"><span data-stu-id="6c0eb-107">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="6c0eb-108">'ndaki Bağlam arabelleğinin ayrılan boyutu.</span><span class="sxs-lookup"><span data-stu-id="6c0eb-108">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="6c0eb-109">dışı Bağlamın gerçek boyutu.</span><span class="sxs-lookup"><span data-stu-id="6c0eb-109">[out] The actual size of the context.</span></span> <span data-ttu-id="6c0eb-110">Bu değer, bağlam arabelleğinin boyutundan küçük veya buna eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c0eb-110">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="6c0eb-111">dışı Bağlam arabelleği.</span><span class="sxs-lookup"><span data-stu-id="6c0eb-111">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c0eb-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6c0eb-112">Return Value</span></span>  

 <span data-ttu-id="6c0eb-113">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c0eb-113">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6c0eb-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c0eb-114">HRESULT</span></span>|<span data-ttu-id="6c0eb-115">Description</span><span class="sxs-lookup"><span data-stu-id="6c0eb-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c0eb-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c0eb-116">S_OK</span></span>|<span data-ttu-id="6c0eb-117">Geçerli çerçevenin bağlamı başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6c0eb-117">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="6c0eb-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c0eb-118">E_FAIL</span></span>|<span data-ttu-id="6c0eb-119">Bağlam döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="6c0eb-119">The context could not be returned.</span></span>|  
|<span data-ttu-id="6c0eb-120">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT ARABELLEĞI)</span><span class="sxs-lookup"><span data-stu-id="6c0eb-120">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="6c0eb-121">Bağlam arabelleği çok küçük.</span><span class="sxs-lookup"><span data-stu-id="6c0eb-121">The context buffer is too small.</span></span>|  
|<span data-ttu-id="6c0eb-122">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="6c0eb-122">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="6c0eb-123">Çerçeve işaretçisi zaten yığının sonunda. Bu nedenle, ek çerçevelere erişilemez.</span><span class="sxs-lookup"><span data-stu-id="6c0eb-123">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="6c0eb-124">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="6c0eb-124">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c0eb-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c0eb-125">Remarks</span></span>  

 <span data-ttu-id="6c0eb-126">Geriye doğru kaldırma, geçici olmayan Yazmaçları gibi yazmaçların yalnızca bir alt kümesini geri yüklediği için, bağlam çağrı sırasında kayıt durumuyla tam olarak eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="6c0eb-126">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c0eb-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c0eb-127">Requirements</span></span>  

 <span data-ttu-id="6c0eb-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c0eb-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c0eb-129">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6c0eb-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c0eb-130">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6c0eb-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c0eb-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c0eb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c0eb-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c0eb-132">See also</span></span>

- [<span data-ttu-id="6c0eb-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6c0eb-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6c0eb-134">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6c0eb-134">Debugging</span></span>](index.md)
