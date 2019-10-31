---
title: 'Icordebugmutabledatatarget:: SetThreadContext yöntemi'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: 2c9e508c7a4059fee4e1cce6eb28e6de7b2fff6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132703"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="d7e0c-102">Icordebugmutabledatatarget:: SetThreadContext yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7e0c-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="d7e0c-103">Bir iş parçacığının bağlamını (kayıt değerlerini) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d7e0c-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7e0c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7e0c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7e0c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d7e0c-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="d7e0c-106">'ndaki İşletim sistemi tanımlı iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d7e0c-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="d7e0c-107">'ndaki Yazılacak `pContext` arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="d7e0c-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="d7e0c-108">'ndaki Yazılacak baytların işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d7e0c-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7e0c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7e0c-109">Remarks</span></span>  
 <span data-ttu-id="d7e0c-110">`SetThreadContext` yöntemi, işletim sistemi tarafından tanımlanan `dwThreadID` bağımsız değişkeni tarafından belirtilen iş parçacığının geçerli bağlamını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="d7e0c-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="d7e0c-111">Bağlam kaydının biçimi [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) yöntemi tarafından belirtilen platforma göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="d7e0c-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="d7e0c-112">Windows 'ta bu bir [bağlam](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="d7e0c-112">On Windows, this is a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7e0c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7e0c-113">Requirements</span></span>  
 <span data-ttu-id="d7e0c-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7e0c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7e0c-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d7e0c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7e0c-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d7e0c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7e0c-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7e0c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7e0c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7e0c-118">See also</span></span>

- [<span data-ttu-id="d7e0c-119">ICorDebugMutableDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7e0c-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="d7e0c-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d7e0c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
