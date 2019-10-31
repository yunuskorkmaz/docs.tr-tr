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
ms.openlocfilehash: 90156152a2c133446dedbe22426785ab63f8dfb9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131805"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="41ad0-102">ICorDebugStackWalk::SetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41ad0-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="41ad0-103">[Icordebugstackyürüme](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesnesinin geçerli bağlamını iş parçacığı için geçerli bir bağlam olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="41ad0-103">Sets the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41ad0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41ad0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41ad0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41ad0-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="41ad0-106">'ndaki Bir [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) bayrağı, bağlamın yığındaki etkin kareden mi yoksa yığının geriye doğru bir şekilde mi devraldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="41ad0-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="41ad0-107">'ndaki `CONTEXT` arabelleğinin ayrılan boyutu.</span><span class="sxs-lookup"><span data-stu-id="41ad0-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="41ad0-108">'ndaki `CONTEXT` arabelleği.</span><span class="sxs-lookup"><span data-stu-id="41ad0-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41ad0-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="41ad0-109">Return Value</span></span>  
 <span data-ttu-id="41ad0-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="41ad0-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="41ad0-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41ad0-111">HRESULT</span></span>|<span data-ttu-id="41ad0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41ad0-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41ad0-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="41ad0-113">S_OK</span></span>|<span data-ttu-id="41ad0-114">`ICorDebugStackWalk` nesnenin bağlamı başarıyla ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="41ad0-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="41ad0-115">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="41ad0-115">E_FAIL</span></span>|<span data-ttu-id="41ad0-116">`ICorDebugStackWalk` nesnenin bağlamı ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="41ad0-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="41ad0-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="41ad0-117">E_INVALIDARG</span></span>|<span data-ttu-id="41ad0-118">Bağlam null.</span><span class="sxs-lookup"><span data-stu-id="41ad0-118">The context is null.</span></span>|  
|<span data-ttu-id="41ad0-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="41ad0-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="41ad0-120">Bağlam arabelleği çok küçük.</span><span class="sxs-lookup"><span data-stu-id="41ad0-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="41ad0-121">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="41ad0-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41ad0-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41ad0-122">Remarks</span></span>  
 <span data-ttu-id="41ad0-123">Bu yöntem, iş parçacığının geçerli bağlamını değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="41ad0-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="41ad0-124">Geçerli içeriğin geçersiz bir bağlam olarak ayarlanması, yığın denetçisi 'nden öngörülemeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="41ad0-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="41ad0-125">[Icordebugstackizlenecek yol:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) yöntemini hemen çağırarak, bu bağlamın tam bit düzeyinde bir kopyasını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41ad0-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41ad0-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41ad0-126">Requirements</span></span>  
 <span data-ttu-id="41ad0-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41ad0-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41ad0-128">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="41ad0-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41ad0-129">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="41ad0-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41ad0-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41ad0-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41ad0-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41ad0-131">See also</span></span>

- [<span data-ttu-id="41ad0-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="41ad0-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="41ad0-133">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="41ad0-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
