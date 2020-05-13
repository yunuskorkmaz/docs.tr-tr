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
ms.openlocfilehash: 743b0c8016ca5c0401046166a770d857215429a3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379216"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="ed318-102">ICorDebugStackWalk::GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed318-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="ed318-103">[Icordebugstackyürüme](icordebugstackwalk-interface.md) nesnesindeki geçerli karenin bağlamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed318-103">Returns the context for the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed318-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed318-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed318-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed318-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="ed318-106">'ndaki Bağlam arabelleğinin istenen içeriğini belirten bayraklar (WinNT. h içinde tanımlanmıştır).</span><span class="sxs-lookup"><span data-stu-id="ed318-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="ed318-107">'ndaki Bağlam arabelleğinin ayrılan boyutu.</span><span class="sxs-lookup"><span data-stu-id="ed318-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="ed318-108">dışı Bağlamın gerçek boyutu.</span><span class="sxs-lookup"><span data-stu-id="ed318-108">[out] The actual size of the context.</span></span> <span data-ttu-id="ed318-109">Bu değer, bağlam arabelleğinin boyutundan küçük veya buna eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed318-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="ed318-110">dışı Bağlam arabelleği.</span><span class="sxs-lookup"><span data-stu-id="ed318-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed318-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ed318-111">Return Value</span></span>  
 <span data-ttu-id="ed318-112">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed318-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ed318-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ed318-113">HRESULT</span></span>|<span data-ttu-id="ed318-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed318-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ed318-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="ed318-115">S_OK</span></span>|<span data-ttu-id="ed318-116">Geçerli çerçevenin bağlamı başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ed318-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="ed318-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ed318-117">E_FAIL</span></span>|<span data-ttu-id="ed318-118">Bağlam döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="ed318-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="ed318-119">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT ARABELLEĞI)</span><span class="sxs-lookup"><span data-stu-id="ed318-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="ed318-120">Bağlam arabelleği çok küçük.</span><span class="sxs-lookup"><span data-stu-id="ed318-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="ed318-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="ed318-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="ed318-122">Çerçeve işaretçisi zaten yığının sonunda. Bu nedenle, ek çerçevelere erişilemez.</span><span class="sxs-lookup"><span data-stu-id="ed318-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="ed318-123">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="ed318-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed318-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed318-124">Remarks</span></span>  
 <span data-ttu-id="ed318-125">Geriye doğru kaldırma, geçici olmayan Yazmaçları gibi yazmaçların yalnızca bir alt kümesini geri yüklediği için, bağlam çağrı sırasında kayıt durumuyla tam olarak eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="ed318-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed318-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed318-126">Requirements</span></span>  
 <span data-ttu-id="ed318-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed318-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed318-128">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ed318-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed318-129">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ed318-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed318-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed318-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed318-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed318-131">See also</span></span>

- [<span data-ttu-id="ed318-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ed318-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ed318-133">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ed318-133">Debugging</span></span>](index.md)
