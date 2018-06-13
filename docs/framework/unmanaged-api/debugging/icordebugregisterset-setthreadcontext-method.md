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
ms.openlocfilehash: 7283266857d81b7d97bcacb56862b50f01cd3f0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419949"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="6fabd-102">ICorDebugRegisterSet::SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6fabd-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="6fabd-103">`SetThreadContext` .NET Framework sürüm 2.0 uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="6fabd-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="6fabd-104">Bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6fabd-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6fabd-105">Üst düzey işlem kullanmak [Icordebugnativeframe::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) bir iş parçacığı bağlamında ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="6fabd-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fabd-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6fabd-106">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="6fabd-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6fabd-107">Requirements</span></span>  
 <span data-ttu-id="6fabd-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fabd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fabd-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6fabd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fabd-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fabd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fabd-111">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="6fabd-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fabd-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6fabd-112">See Also</span></span>  
 [<span data-ttu-id="6fabd-113">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6fabd-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="6fabd-114">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6fabd-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
