---
description: ': ICorDebugRegisterSet:: GetThreadContext metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: be6384562858d04b6e139eda83c172c09f2dfc0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690814"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="ec4c2-103">ICorDebugRegisterSet::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="ec4c2-103">ICorDebugRegisterSet::GetThreadContext Method</span></span>

<span data-ttu-id="ec4c2-104">Geçerli iş parçacığının bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="ec4c2-104">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec4c2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec4c2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec4c2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec4c2-106">Parameters</span></span>  

 `contextSize`  
 <span data-ttu-id="ec4c2-107">'ndaki Dizinin bayt cinsinden boyutu `context` .</span><span class="sxs-lookup"><span data-stu-id="ec4c2-107">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="ec4c2-108">[in, out] Geçerli platform için Win32 yapısını oluşturan bir bayt dizisi `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="ec4c2-108">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec4c2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec4c2-109">Remarks</span></span>  

 <span data-ttu-id="ec4c2-110">`GetThreadContext`İş parçacığı, bağlamı geçici olarak değiştirilen bir "ele geçirilmiş" durumda olabileceğinden, hata ayıklayıcı Win32 işlevi yerine bu işlevi çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ec4c2-110">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="ec4c2-111">Döndürülen veriler, `CONTEXT` geçerli platform için bir Win32 yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="ec4c2-111">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="ec4c2-112">Yaprak olmayan kareler için, istemciler [ICorDebugRegisterSet:: GetRegistersAvailable](icordebugregisterset-getregistersavailable-method.md)kullanarak hangi yazmaçların geçerli olduğunu denetlemelidir.</span><span class="sxs-lookup"><span data-stu-id="ec4c2-112">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec4c2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec4c2-113">Requirements</span></span>  

 <span data-ttu-id="ec4c2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec4c2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec4c2-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ec4c2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec4c2-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ec4c2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec4c2-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec4c2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec4c2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec4c2-118">See also</span></span>

- [<span data-ttu-id="ec4c2-119">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec4c2-119">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="ec4c2-120">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec4c2-120">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
