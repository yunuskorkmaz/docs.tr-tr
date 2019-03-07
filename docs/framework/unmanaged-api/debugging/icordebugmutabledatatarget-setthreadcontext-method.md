---
title: ICorDebugMutableDataTarget::SetThreadContext yöntemi
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbbe4dcec29ba85c64b6e22a4348c56e80daf623
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479201"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="6c5c8-102">ICorDebugMutableDataTarget::SetThreadContext yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c5c8-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="6c5c8-103">Bir iş parçacığı bağlamı (yazmaç değerlerini) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6c5c8-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c5c8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c5c8-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c5c8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c5c8-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="6c5c8-106">[in] İşletim sistemi tarafından tanımlanan iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6c5c8-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="6c5c8-107">[in] Boyutu `pContext` arabelleğe yazılacak.</span><span class="sxs-lookup"><span data-stu-id="6c5c8-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="6c5c8-108">[in] Yazılacak bayt için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6c5c8-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c5c8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c5c8-109">Remarks</span></span>  
 <span data-ttu-id="6c5c8-110">`SetThreadContext` Yöntemi güncelleştirmeleri işletim sistemi tarafından tanımlanan tarafından belirtilen iş parçacığı için geçerli bağlam `dwThreadID` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="6c5c8-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="6c5c8-111">Bağlam kaydı biçimi tarafından belirtilen platform tarafından belirlenir [Icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6c5c8-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="6c5c8-112">Windows üzerinde bu, bir [bağlam](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) yapısı.</span><span class="sxs-lookup"><span data-stu-id="6c5c8-112">On Windows, this is a [CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c5c8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c5c8-113">Requirements</span></span>  
 <span data-ttu-id="6c5c8-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c5c8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c5c8-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c5c8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c5c8-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c5c8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c5c8-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c5c8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c5c8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c5c8-118">See also</span></span>
- [<span data-ttu-id="6c5c8-119">ICorDebugMutableDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c5c8-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="6c5c8-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6c5c8-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
