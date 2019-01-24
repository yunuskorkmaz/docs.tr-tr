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
ms.openlocfilehash: 6ee62c903da2f2568884b9be30b22bdcdc2d2c4b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686276"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="d5a7d-102">ICorDebugRegisterSet::SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5a7d-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="d5a7d-103">`SetThreadContext` .NET Framework 2.0 sürümünde uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="d5a7d-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="d5a7d-104">Bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d5a7d-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5a7d-105">Üst düzey işlem kullanın [Icordebugnativeframe::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) iş parçacığı bağlamını ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="d5a7d-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5a7d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5a7d-106">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d5a7d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5a7d-107">Requirements</span></span>  
 <span data-ttu-id="d5a7d-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5a7d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5a7d-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5a7d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5a7d-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5a7d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5a7d-111">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="d5a7d-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5a7d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5a7d-112">See also</span></span>
- [<span data-ttu-id="d5a7d-113">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5a7d-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="d5a7d-114">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5a7d-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
