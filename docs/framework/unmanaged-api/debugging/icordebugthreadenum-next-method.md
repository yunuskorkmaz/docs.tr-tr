---
title: ICorDebugThreadEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum::Next
helpviewer_keywords:
- ICorDebugThreadEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: f967c93d-9a7f-4aaf-99a1-a1317899ff3f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 050bfb08dfd95e29b6534f69dbd35400d59e6099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419610"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="7cb6d-102">ICorDebugThreadEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7cb6d-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="7cb6d-103">Geçerli konumdan başlayarak numaralandırma, belirtilen Icordebugthread örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="7cb6d-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cb6d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7cb6d-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7cb6d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7cb6d-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7cb6d-106">[in] Sayısı `ICorDebugThread` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7cb6d-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="7cb6d-107">[out] Her biri işaret işaretçileri, bir dizi bir `ICorDebugThread` bir iş parçacığı temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="7cb6d-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7cb6d-108">[out] İşaretçi sayısına `ICorDebugThread` gerçekte döndürülen örnek.</span><span class="sxs-lookup"><span data-stu-id="7cb6d-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="7cb6d-109">Bu değer null ise `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="7cb6d-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cb6d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7cb6d-110">Requirements</span></span>  
 <span data-ttu-id="7cb6d-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cb6d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cb6d-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7cb6d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cb6d-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cb6d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cb6d-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cb6d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
