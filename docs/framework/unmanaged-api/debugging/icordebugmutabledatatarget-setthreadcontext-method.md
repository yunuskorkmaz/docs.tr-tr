---
title: "ICorDebugMutableDataTarget::SetThreadContext yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8c43ef5405ed582cc55af69d7f41887c0615965f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="b9e8d-102">ICorDebugMutableDataTarget::SetThreadContext yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9e8d-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="b9e8d-103">Bir iş parçacığı bağlamının (kayıt değerlerini) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b9e8d-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9e8d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9e8d-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9e8d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9e8d-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="b9e8d-106">[in] İşletim sistemi tarafından tanımlanan iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="b9e8d-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="b9e8d-107">[in] Boyutunu `pContext` yazılacak arabellek.</span><span class="sxs-lookup"><span data-stu-id="b9e8d-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="b9e8d-108">[in] Yazılacak bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b9e8d-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9e8d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9e8d-109">Remarks</span></span>  
 <span data-ttu-id="b9e8d-110">`SetThreadContext` Yöntemi güncelleştirmeleri işletim sistemi tarafından tanımlanan tarafından belirtilen iş parçacığı için geçerli bağlam `dwThreadID` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="b9e8d-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="b9e8d-111">İçerik kaydı biçimi tarafından belirtilen platform tarafından belirlenen [Icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b9e8d-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="b9e8d-112">Windows üzerinde bu olan bir [BAĞLAMI](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="b9e8d-112">On Windows, this is a [CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9e8d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9e8d-113">Requirements</span></span>  
 <span data-ttu-id="b9e8d-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9e8d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9e8d-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9e8d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9e8d-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9e8d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9e8d-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9e8d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9e8d-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b9e8d-118">See Also</span></span>  
 [<span data-ttu-id="b9e8d-119">ICorDebugMutableDataTarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9e8d-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="b9e8d-120">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b9e8d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
