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
ms.openlocfilehash: faacea6a2f04ef20025fd33adb4ce76eaf54f32c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679747"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="87f59-102">ICorDebugDataTarget::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="87f59-102">ICorDebugDataTarget::GetThreadContext Method</span></span>

<span data-ttu-id="87f59-103">Belirtilen iş parçacığı için geçerli iş parçacığı bağlamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="87f59-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87f59-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="87f59-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87f59-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87f59-105">Parameters</span></span>  

 `dwThreadID`  
 <span data-ttu-id="87f59-106">'ndaki Bağlamını alınacak olan iş parçacığının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="87f59-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="87f59-107">Tanımlayıcı, işletim sistemi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="87f59-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="87f59-108">'ndaki İçeriğin hangi bölümlerinin okunabileceği belirten, platforma bağımlı bayrakların bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="87f59-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="87f59-109">'ndaki Boyutu `pContext` .</span><span class="sxs-lookup"><span data-stu-id="87f59-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="87f59-110">dışı İş parçacığı bağlamının depolanacağı arabellek.</span><span class="sxs-lookup"><span data-stu-id="87f59-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87f59-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87f59-111">Remarks</span></span>  

 <span data-ttu-id="87f59-112">Windows platformlarında, `pContext` `CONTEXT` [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından belirtilen makine türüne uygun bir yapı (Winnt. h içinde tanımlanır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="87f59-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="87f59-113">`contextFlags` yapının alanıyla aynı değerlere sahip olmalıdır `ContextFlags` `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="87f59-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="87f59-114">`CONTEXT`Yapı, işlemciye özeldir; Ayrıntılar Için Winnt. h dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="87f59-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87f59-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87f59-115">Requirements</span></span>  

 <span data-ttu-id="87f59-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87f59-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87f59-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="87f59-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87f59-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="87f59-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87f59-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87f59-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f59-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87f59-120">See also</span></span>

- [<span data-ttu-id="87f59-121">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87f59-121">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="87f59-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="87f59-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="87f59-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="87f59-123">Debugging</span></span>](index.md)
