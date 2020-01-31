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
ms.openlocfilehash: 8137d5477b75b864e223852cf524ac8c5b6c0f2b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792085"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="d668f-102">ICorDebugRegisterSet::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="d668f-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="d668f-103">Geçerli iş parçacığının bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="d668f-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d668f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d668f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d668f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d668f-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="d668f-106">'ndaki `context` dizisinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="d668f-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="d668f-107">[in, out] Geçerli platform için Win32 `CONTEXT` yapısını oluşturan bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="d668f-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d668f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d668f-108">Remarks</span></span>  
 <span data-ttu-id="d668f-109">İş parçacığı, bağlamı geçici olarak değiştirilen bir "ele geçirilmiş" durumda olabileceğinden, hata ayıklayıcı Win32 `GetThreadContext` işlevi yerine bu işlevi çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d668f-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="d668f-110">Döndürülen veriler, geçerli platform için bir Win32 `CONTEXT` yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="d668f-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="d668f-111">Yaprak olmayan kareler için, istemciler [ICorDebugRegisterSet:: GetRegistersAvailable](icordebugregisterset-getregistersavailable-method.md)kullanarak hangi yazmaçların geçerli olduğunu denetlemelidir.</span><span class="sxs-lookup"><span data-stu-id="d668f-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d668f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d668f-112">Requirements</span></span>  
 <span data-ttu-id="d668f-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d668f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d668f-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d668f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d668f-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d668f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d668f-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d668f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d668f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d668f-117">See also</span></span>

- [<span data-ttu-id="d668f-118">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d668f-118">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="d668f-119">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d668f-119">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
