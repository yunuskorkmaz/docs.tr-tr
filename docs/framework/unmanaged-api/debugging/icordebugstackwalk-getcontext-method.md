---
title: ICorDebugStackWalk::GetContext Metodu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
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
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 080ce39422faee4e1228bd87bf994080fab4de71
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/10/2018
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="8a0f3-102">ICorDebugStackWalk::GetContext Metodu</span><span class="sxs-lookup"><span data-stu-id="8a0f3-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="8a0f3-103">Geçerli kare bağlamının döndürür [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="8a0f3-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a0f3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a0f3-104">Syntax</span></span>  
  
```  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a0f3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8a0f3-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="8a0f3-106">[in] (WinNT.h içinde tanımlanmıştır) bağlamı arabelleğine istenen içeriği gösterir bayraklar.</span><span class="sxs-lookup"><span data-stu-id="8a0f3-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="8a0f3-107">[in] Bağlamı arabelleğine tahsis edilen boyutu.</span><span class="sxs-lookup"><span data-stu-id="8a0f3-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="8a0f3-108">[out] Bağlam gerçek boyutu.</span><span class="sxs-lookup"><span data-stu-id="8a0f3-108">[out] The actual size of the context.</span></span> <span data-ttu-id="8a0f3-109">Bu değer bağlam arabellek boyutu eşit veya daha az olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a0f3-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="8a0f3-110">[out] Bağlam arabelleği.</span><span class="sxs-lookup"><span data-stu-id="8a0f3-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a0f3-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8a0f3-111">Return Value</span></span>  
 <span data-ttu-id="8a0f3-112">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="8a0f3-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8a0f3-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8a0f3-113">HRESULT</span></span>|<span data-ttu-id="8a0f3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a0f3-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8a0f3-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="8a0f3-115">S_OK</span></span>|<span data-ttu-id="8a0f3-116">Geçerli çerçeve bağlamının başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8a0f3-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="8a0f3-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8a0f3-117">E_FAIL</span></span>|<span data-ttu-id="8a0f3-118">Bağlam döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="8a0f3-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="8a0f3-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="8a0f3-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="8a0f3-120">Bağlam arabellek çok küçük.</span><span class="sxs-lookup"><span data-stu-id="8a0f3-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="8a0f3-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="8a0f3-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="8a0f3-122">Çerçeve işaretçisi yığının sonuna zaten; Bu nedenle, hiçbir ek çerçeve erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="8a0f3-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="8a0f3-123">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="8a0f3-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a0f3-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a0f3-124">Remarks</span></span>  
 <span data-ttu-id="8a0f3-125">Geriye doğru izleme geçici olmayan Yazmaçları gibi kayıtları yalnızca bir kısmı getirir çünkü bağlam tam kayıt durumu çağrı aynı anda aynı olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8a0f3-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a0f3-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a0f3-126">Requirements</span></span>  
 <span data-ttu-id="8a0f3-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a0f3-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a0f3-128">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a0f3-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a0f3-129">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a0f3-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a0f3-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a0f3-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a0f3-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a0f3-131">See Also</span></span>  
 [<span data-ttu-id="8a0f3-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8a0f3-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8a0f3-133">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8a0f3-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
