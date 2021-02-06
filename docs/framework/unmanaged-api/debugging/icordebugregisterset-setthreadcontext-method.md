---
description: ': ICorDebugRegisterSet:: SetThreadContext yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8d874b1864e85e477260632ad6012dbbf10aefb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637696"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="417e1-103">ICorDebugRegisterSet::SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="417e1-103">ICorDebugRegisterSet::SetThreadContext Method</span></span>

<span data-ttu-id="417e1-104">`SetThreadContext` .NET Framework sürüm 2,0 ' de uygulanmıyor.</span><span class="sxs-lookup"><span data-stu-id="417e1-104">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="417e1-105">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="417e1-105">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="417e1-106">Bir iş parçacığının bağlamını ayarlamak için [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md) üst düzey işlemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="417e1-106">Use the higher-level operation [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="417e1-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="417e1-107">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="417e1-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="417e1-108">Requirements</span></span>  

 <span data-ttu-id="417e1-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="417e1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="417e1-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="417e1-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="417e1-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="417e1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="417e1-112">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="417e1-112">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="417e1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="417e1-113">See also</span></span>

- [<span data-ttu-id="417e1-114">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="417e1-114">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="417e1-115">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="417e1-115">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
