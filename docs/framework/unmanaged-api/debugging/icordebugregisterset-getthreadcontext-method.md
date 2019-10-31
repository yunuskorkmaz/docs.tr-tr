---
title: ICorDebugRegisterSet::GetThreadContext Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
ms.openlocfilehash: db4f9bc6277015055cbcdb509628f2862a71dbc4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127160"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="e842b-102">ICorDebugRegisterSet::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="e842b-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="e842b-103">Geçerli iş parçacığının bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="e842b-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e842b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e842b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e842b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e842b-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="e842b-106">'ndaki `context` dizisinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="e842b-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="e842b-107">[in, out] Geçerli platform için Win32 `CONTEXT` yapısını oluşturan bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="e842b-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e842b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e842b-108">Remarks</span></span>  
 <span data-ttu-id="e842b-109">İş parçacığı, bağlamı geçici olarak değiştirilen bir "ele geçirilmiş" durumda olabileceğinden, hata ayıklayıcı Win32 `GetThreadContext` işlevi yerine bu işlevi çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e842b-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="e842b-110">Döndürülen veriler, geçerli platform için bir Win32 `CONTEXT` yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="e842b-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="e842b-111">Yaprak olmayan kareler için, istemciler [ICorDebugRegisterSet:: GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)kullanarak hangi yazmaçların geçerli olduğunu denetlemelidir.</span><span class="sxs-lookup"><span data-stu-id="e842b-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e842b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e842b-112">Requirements</span></span>  
 <span data-ttu-id="e842b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e842b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e842b-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e842b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e842b-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e842b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e842b-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e842b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e842b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e842b-117">See also</span></span>

- [<span data-ttu-id="e842b-118">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e842b-118">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="e842b-119">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e842b-119">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
