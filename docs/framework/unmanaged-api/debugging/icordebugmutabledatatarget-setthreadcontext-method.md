---
title: 'Icordebugmutabledatatarget:: SetThreadContext yöntemi'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: 558a1ee2eb0ac06213c2ebcebbd5595b69ecc43e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695716"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="a3f88-102">Icordebugmutabledatatarget:: SetThreadContext yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3f88-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>

<span data-ttu-id="a3f88-103">Bir iş parçacığının bağlamını (kayıt değerlerini) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a3f88-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3f88-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a3f88-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3f88-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3f88-105">Parameters</span></span>  

 `dwThreadID`  
 <span data-ttu-id="a3f88-106">'ndaki İşletim sistemi tanımlı iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a3f88-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="a3f88-107">'ndaki `pContext` Yazılacak arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="a3f88-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="a3f88-108">'ndaki Yazılacak baytların işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a3f88-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3f88-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3f88-109">Remarks</span></span>  

 <span data-ttu-id="a3f88-110">`SetThreadContext`Yöntemi, işletim sistemi tarafından tanımlanan bağımsız değişken tarafından belirtilen iş parçacığının geçerli bağlamını güncelleştirir `dwThreadID` .</span><span class="sxs-lookup"><span data-stu-id="a3f88-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="a3f88-111">Bağlam kaydının biçimi [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından belirtilen platforma göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="a3f88-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="a3f88-112">Windows 'ta bu bir [bağlam](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="a3f88-112">On Windows, this is a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3f88-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3f88-113">Requirements</span></span>  

 <span data-ttu-id="a3f88-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3f88-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3f88-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a3f88-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3f88-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a3f88-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3f88-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3f88-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3f88-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3f88-118">See also</span></span>

- [<span data-ttu-id="a3f88-119">ICorDebugMutableDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3f88-119">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="a3f88-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a3f88-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
