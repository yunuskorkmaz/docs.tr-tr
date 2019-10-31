---
title: ICorDebugRegisterSet::SetThreadContext Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type:
- apiref
ms.openlocfilehash: 8731b57206f7987efc2498a5abe62295cd1cfae5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131333"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="6a21b-102">ICorDebugRegisterSet::SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a21b-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="6a21b-103">`SetThreadContext`, .NET Framework sürüm 2,0 ' de uygulanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="6a21b-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="6a21b-104">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="6a21b-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a21b-105">Bir iş parçacığının bağlamını ayarlamak için [ICorDebugNativeFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) üst düzey işlemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a21b-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a21b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a21b-106">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="6a21b-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a21b-107">Requirements</span></span>  
 <span data-ttu-id="6a21b-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a21b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a21b-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6a21b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a21b-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6a21b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a21b-111">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="6a21b-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a21b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a21b-112">See also</span></span>

- [<span data-ttu-id="6a21b-113">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a21b-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="6a21b-114">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a21b-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
