---
description: ': Icordebugmutabledatatarget:: SetThreadContext yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugmutabledatatarget:: SetThreadContext yöntemi'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: 4674df92b72b44e19eff663c9a17dd8ca4b5a1b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722483"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="6513b-103">Icordebugmutabledatatarget:: SetThreadContext yöntemi</span><span class="sxs-lookup"><span data-stu-id="6513b-103">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>

<span data-ttu-id="6513b-104">Bir iş parçacığının bağlamını (kayıt değerlerini) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6513b-104">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6513b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6513b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6513b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6513b-106">Parameters</span></span>  

 `dwThreadID`  
 <span data-ttu-id="6513b-107">'ndaki İşletim sistemi tanımlı iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6513b-107">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="6513b-108">'ndaki `pContext` Yazılacak arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="6513b-108">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="6513b-109">'ndaki Yazılacak baytların işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6513b-109">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6513b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6513b-110">Remarks</span></span>  

 <span data-ttu-id="6513b-111">`SetThreadContext`Yöntemi, işletim sistemi tarafından tanımlanan bağımsız değişken tarafından belirtilen iş parçacığının geçerli bağlamını güncelleştirir `dwThreadID` .</span><span class="sxs-lookup"><span data-stu-id="6513b-111">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="6513b-112">Bağlam kaydının biçimi [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından belirtilen platforma göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6513b-112">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="6513b-113">Windows 'ta bu bir [bağlam](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="6513b-113">On Windows, this is a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6513b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6513b-114">Requirements</span></span>  

 <span data-ttu-id="6513b-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6513b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6513b-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6513b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6513b-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6513b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6513b-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6513b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6513b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6513b-119">See also</span></span>

- [<span data-ttu-id="6513b-120">ICorDebugMutableDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6513b-120">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="6513b-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6513b-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
