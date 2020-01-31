---
title: ICorDebugDataTarget::GetThreadContext Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
ms.openlocfilehash: 3eace2d91b3bb6e637a659b8b49a31450ebc2c42
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783725"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="76bb5-102">ICorDebugDataTarget::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="76bb5-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="76bb5-103">Belirtilen iş parçacığı için geçerli iş parçacığı bağlamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="76bb5-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76bb5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76bb5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76bb5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="76bb5-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="76bb5-106">'ndaki Bağlamını alınacak olan iş parçacığının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="76bb5-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="76bb5-107">Tanımlayıcı, işletim sistemi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="76bb5-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="76bb5-108">'ndaki İçeriğin hangi bölümlerinin okunabileceği belirten, platforma bağımlı bayrakların bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="76bb5-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="76bb5-109">'ndaki `pContext`boyutu.</span><span class="sxs-lookup"><span data-stu-id="76bb5-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="76bb5-110">dışı İş parçacığı bağlamının depolanacağı arabellek.</span><span class="sxs-lookup"><span data-stu-id="76bb5-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76bb5-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76bb5-111">Remarks</span></span>  
 <span data-ttu-id="76bb5-112">Windows platformlarında, `pContext` [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından belirtilen makine türü için uygun bir `CONTEXT` yapısı (Winnt. h içinde tanımlanır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="76bb5-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="76bb5-113">`contextFlags`, `CONTEXT` yapısının `ContextFlags` alanıyla aynı değerlere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="76bb5-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="76bb5-114">`CONTEXT` yapısı, işlemciye özeldir; Ayrıntılar için WinNT. h dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="76bb5-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76bb5-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76bb5-115">Requirements</span></span>  
 <span data-ttu-id="76bb5-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76bb5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76bb5-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="76bb5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76bb5-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="76bb5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76bb5-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76bb5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76bb5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76bb5-120">See also</span></span>

- [<span data-ttu-id="76bb5-121">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76bb5-121">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="76bb5-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="76bb5-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="76bb5-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="76bb5-123">Debugging</span></span>](index.md)
