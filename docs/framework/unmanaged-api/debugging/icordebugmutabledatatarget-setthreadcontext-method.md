---
title: ICorDebugMutableDataTarget::SetThreadContext yöntemi
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3826bacb935652a282eac359170d9b93518e5cd
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931804"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="eb519-102">ICorDebugMutableDataTarget::SetThreadContext yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb519-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="eb519-103">Bir iş parçacığı bağlamı (yazmaç değerlerini) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="eb519-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb519-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb519-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb519-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb519-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="eb519-106">[in] İşletim sistemi tarafından tanımlanan iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="eb519-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="eb519-107">[in] Boyutu `pContext` arabelleğe yazılacak.</span><span class="sxs-lookup"><span data-stu-id="eb519-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="eb519-108">[in] Yazılacak bayt için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eb519-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb519-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb519-109">Remarks</span></span>  
 <span data-ttu-id="eb519-110">`SetThreadContext` Yöntemi güncelleştirmeleri işletim sistemi tarafından tanımlanan tarafından belirtilen iş parçacığı için geçerli bağlam `dwThreadID` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="eb519-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="eb519-111">Bağlam kaydı biçimi tarafından belirtilen platform tarafından belirlenir [Icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="eb519-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="eb519-112">Windows üzerinde bu, bir [bağlam](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) yapısı.</span><span class="sxs-lookup"><span data-stu-id="eb519-112">On Windows, this is a [CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb519-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb519-113">Requirements</span></span>  
 <span data-ttu-id="eb519-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb519-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb519-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb519-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb519-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb519-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb519-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb519-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb519-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb519-118">See Also</span></span>  
 [<span data-ttu-id="eb519-119">ICorDebugMutableDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb519-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="eb519-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eb519-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
