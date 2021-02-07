---
description: ': ICorDebugDataTarget:: GetThreadContext metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: cf40579aa0a495af4e5e775334d177ca6f3da86f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710640"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="7bc00-103">ICorDebugDataTarget::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="7bc00-103">ICorDebugDataTarget::GetThreadContext Method</span></span>

<span data-ttu-id="7bc00-104">Belirtilen iş parçacığı için geçerli iş parçacığı bağlamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7bc00-104">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bc00-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7bc00-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bc00-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7bc00-106">Parameters</span></span>  

 `dwThreadID`  
 <span data-ttu-id="7bc00-107">'ndaki Bağlamını alınacak olan iş parçacığının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7bc00-107">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="7bc00-108">Tanımlayıcı, işletim sistemi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7bc00-108">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="7bc00-109">'ndaki İçeriğin hangi bölümlerinin okunabileceği belirten, platforma bağımlı bayrakların bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="7bc00-109">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="7bc00-110">'ndaki Boyutu `pContext` .</span><span class="sxs-lookup"><span data-stu-id="7bc00-110">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="7bc00-111">dışı İş parçacığı bağlamının depolanacağı arabellek.</span><span class="sxs-lookup"><span data-stu-id="7bc00-111">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bc00-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bc00-112">Remarks</span></span>  

 <span data-ttu-id="7bc00-113">Windows platformlarında, `pContext` `CONTEXT` [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından belirtilen makine türüne uygun bir yapı (Winnt. h içinde tanımlanır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7bc00-113">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="7bc00-114">`contextFlags` yapının alanıyla aynı değerlere sahip olmalıdır `ContextFlags` `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="7bc00-114">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="7bc00-115">`CONTEXT`Yapı, işlemciye özeldir; Ayrıntılar Için Winnt. h dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="7bc00-115">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bc00-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7bc00-116">Requirements</span></span>  

 <span data-ttu-id="7bc00-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bc00-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bc00-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7bc00-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bc00-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7bc00-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bc00-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bc00-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bc00-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bc00-121">See also</span></span>

- [<span data-ttu-id="7bc00-122">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7bc00-122">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="7bc00-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7bc00-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7bc00-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7bc00-124">Debugging</span></span>](index.md)
