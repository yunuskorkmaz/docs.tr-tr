---
title: ICorDebugStackWalk::SetContext Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6025a31f26c635ac40dcc2e35e7017be1c81feba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423022"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="0c30c-102">ICorDebugStackWalk::SetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c30c-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="0c30c-103">Ayarlar [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesnenin iş parçacığı için geçerli bir bağlam için geçerli bağlam.</span><span class="sxs-lookup"><span data-stu-id="0c30c-103">Sets the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c30c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c30c-104">Syntax</span></span>  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c30c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0c30c-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="0c30c-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) yığında etkin çerçeveden bağlam mi yoksa bir bağlam elde yığını geriye doğru izleme tarafından mı olduğunu belirten bayrak.</span><span class="sxs-lookup"><span data-stu-id="0c30c-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="0c30c-107">[in] Ayrılmış boyutu `CONTEXT` arabellek.</span><span class="sxs-lookup"><span data-stu-id="0c30c-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="0c30c-108">[in] `CONTEXT` Arabellek.</span><span class="sxs-lookup"><span data-stu-id="0c30c-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c30c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0c30c-109">Return Value</span></span>  
 <span data-ttu-id="0c30c-110">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="0c30c-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0c30c-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c30c-111">HRESULT</span></span>|<span data-ttu-id="0c30c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c30c-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c30c-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c30c-113">S_OK</span></span>|<span data-ttu-id="0c30c-114">`ICorDebugStackWalk` Nesnenin içerik başarıyla ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="0c30c-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="0c30c-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0c30c-115">E_FAIL</span></span>|<span data-ttu-id="0c30c-116">`ICorDebugStackWalk` Nesnenin bağlam ayarlanamadı.</span><span class="sxs-lookup"><span data-stu-id="0c30c-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="0c30c-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0c30c-117">E_INVALIDARG</span></span>|<span data-ttu-id="0c30c-118">Bağlamı null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="0c30c-118">The context is null.</span></span>|  
|<span data-ttu-id="0c30c-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="0c30c-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="0c30c-120">Bağlam arabellek çok küçük.</span><span class="sxs-lookup"><span data-stu-id="0c30c-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="0c30c-121">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="0c30c-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c30c-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c30c-122">Remarks</span></span>  
 <span data-ttu-id="0c30c-123">Bu yöntem, geçerli iş parçacığının içeriği değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="0c30c-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="0c30c-124">Geçerli bağlam için geçersiz bir bağlam ayarı yığını walker öngörülemeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0c30c-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="0c30c-125">Hemen çağırarak bu bağlamda tam bir bit düzeyinde kopyasını alabilirsiniz [Icordebugstackwalk::getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0c30c-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c30c-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c30c-126">Requirements</span></span>  
 <span data-ttu-id="0c30c-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c30c-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c30c-128">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c30c-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c30c-129">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c30c-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c30c-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c30c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c30c-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0c30c-131">See Also</span></span>  
 [<span data-ttu-id="0c30c-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0c30c-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0c30c-133">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0c30c-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
