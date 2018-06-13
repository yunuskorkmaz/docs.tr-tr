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
ms.openlocfilehash: 632d3912bae28da22e701078bb47d2d8dbfd3644
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423409"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="85891-102">ICorDebugRegisterSet::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="85891-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="85891-103">Geçerli iş parçacığının bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="85891-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85891-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85891-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85891-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="85891-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="85891-106">[in] Bayt olarak boyutu, `context` dizi.</span><span class="sxs-lookup"><span data-stu-id="85891-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="85891-107">[içinde out] Win32 oluşturan bir bayt dizisi `CONTEXT` geçerli platform için yapısı.</span><span class="sxs-lookup"><span data-stu-id="85891-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85891-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85891-108">Remarks</span></span>  
 <span data-ttu-id="85891-109">Hata ayıklayıcı Win32 yerine bu işlev çağırmalıdır `GetThreadContext` işlev çünkü iş parçacığı burada onun içeriği geçici olarak değiştirildi "ele geçirilen" bir durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="85891-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="85891-110">Döndürülen veriler bir Win32 olduğu `CONTEXT` geçerli platform için yapısı.</span><span class="sxs-lookup"><span data-stu-id="85891-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="85891-111">Yaprak olmayan çerçeveler için istemcileri kullanarak hangi kayıtları geçerli denetlemelisiniz [Icordebugregisterset::getregistersavailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span><span class="sxs-lookup"><span data-stu-id="85891-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85891-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85891-112">Requirements</span></span>  
 <span data-ttu-id="85891-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85891-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85891-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85891-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85891-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85891-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85891-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85891-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85891-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="85891-117">See Also</span></span>  
 [<span data-ttu-id="85891-118">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85891-118">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="85891-119">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85891-119">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
