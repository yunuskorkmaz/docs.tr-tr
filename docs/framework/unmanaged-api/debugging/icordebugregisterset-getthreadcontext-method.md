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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 668b3849af9be24e019dc472a0b80067f0e1e0c1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612742"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="e9309-102">ICorDebugRegisterSet::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="e9309-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="e9309-103">Geçerli iş parçacığı bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="e9309-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9309-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9309-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9309-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9309-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="e9309-106">[in] Bayt cinsinden boyutu, `context` dizisi.</span><span class="sxs-lookup"><span data-stu-id="e9309-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="e9309-107">[out içinde] Win32 oluşturan bir bayt dizisi `CONTEXT` geçerli platform için yapısı.</span><span class="sxs-lookup"><span data-stu-id="e9309-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9309-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9309-108">Remarks</span></span>  
 <span data-ttu-id="e9309-109">Hata ayıklayıcı Win32 yerine bu işlevi çağırmanız gerekir `GetThreadContext` işlev çünkü iş parçacığı burada onun içeriği geçici olarak değiştirildi "ele geçirilen" bir durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="e9309-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="e9309-110">Döndürülen veriler bir Win32, `CONTEXT` geçerli platform için yapısı.</span><span class="sxs-lookup"><span data-stu-id="e9309-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="e9309-111">Yaprak olmayan çerçeveler için istemcileri hangi kayıtları kullanarak geçerli olduğunu denetlemeniz gerekir [Icordebugregisterset::getregistersavailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span><span class="sxs-lookup"><span data-stu-id="e9309-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9309-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9309-112">Requirements</span></span>  
 <span data-ttu-id="e9309-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9309-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9309-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9309-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9309-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9309-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9309-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9309-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9309-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9309-117">See also</span></span>
- [<span data-ttu-id="e9309-118">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9309-118">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="e9309-119">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9309-119">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
