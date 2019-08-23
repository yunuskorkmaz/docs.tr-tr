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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff1365ddb46ca28cbcaa4f1383b293681e6ec214
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956781"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="2e5f7-102">ICorDebugRegisterSet::SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e5f7-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="2e5f7-103">`SetThreadContext`.NET Framework sürüm 2,0 ' de uygulanmıyor.</span><span class="sxs-lookup"><span data-stu-id="2e5f7-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="2e5f7-104">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="2e5f7-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e5f7-105">Bir iş parçacığının bağlamını ayarlamak için [ICorDebugNativeFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) üst düzey işlemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2e5f7-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e5f7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e5f7-106">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2e5f7-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e5f7-107">Requirements</span></span>  
 <span data-ttu-id="2e5f7-108">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e5f7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e5f7-109">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2e5f7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e5f7-110">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2e5f7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e5f7-111">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="2e5f7-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e5f7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e5f7-112">See also</span></span>

- [<span data-ttu-id="2e5f7-113">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e5f7-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="2e5f7-114">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e5f7-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
