---
title: ICorDebugChain::GetNext Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetNext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetNext
helpviewer_keywords:
- GetNext method [.NET Framework debugging]
- ICorDebugChain::GetNext method [.NET Framework debugging]
ms.assetid: 8d9744a5-e08b-4ab2-9855-5c22711cc1e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 839052b72d908e48a4b6f88dab05ec3c3d575d65
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405417"
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="54acb-102">ICorDebugChain::GetNext Metodu</span><span class="sxs-lookup"><span data-stu-id="54acb-102">ICorDebugChain::GetNext Method</span></span>
<span data-ttu-id="54acb-103">Çerçeve sonraki zincirine iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="54acb-103">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54acb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54acb-104">Syntax</span></span>  
  
```  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54acb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54acb-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="54acb-106">[out] Bir işaretçi adresine Icordebugchain nesnenin iş parçacığı için çerçeveler sonraki zincirine temsil eder.</span><span class="sxs-lookup"><span data-stu-id="54acb-106">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="54acb-107">Bu zincirdeki son zinciri ise `ppChain` null.</span><span class="sxs-lookup"><span data-stu-id="54acb-107">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54acb-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54acb-108">Requirements</span></span>  
 <span data-ttu-id="54acb-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54acb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54acb-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54acb-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54acb-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54acb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54acb-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54acb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
