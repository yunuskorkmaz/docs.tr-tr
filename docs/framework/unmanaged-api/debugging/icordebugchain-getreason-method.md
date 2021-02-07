---
description: ': Icordebugzincirine:: GetReason Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugChain::GetReason Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- GetReason
helpviewer_keywords:
- GetReason method [.NET Framework debugging]
- ICorDebugChain::GetReason method [.NET Framework debugging]
ms.assetid: 9f9f62b9-113a-4a98-8f9b-b593cef27b03
topic_type:
- apiref
ms.openlocfilehash: 0952d09db6d43f7970ba9e8c46c409fb2cd4b131
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694975"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="bf4f1-103">ICorDebugChain::GetReason Metodu</span><span class="sxs-lookup"><span data-stu-id="bf4f1-103">ICorDebugChain::GetReason Method</span></span>

<span data-ttu-id="bf4f1-104">Bu çağrı zincirinin Genesin nedenini alır.</span><span class="sxs-lookup"><span data-stu-id="bf4f1-104">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf4f1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf4f1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf4f1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bf4f1-106">Parameters</span></span>  

 `pReason`  
 <span data-ttu-id="bf4f1-107">dışı Bu çağrı zincirinin Genesin nedenini gösteren bir değer işaretçisi (bit düzeyinde bir bileşim).</span><span class="sxs-lookup"><span data-stu-id="bf4f1-107">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf4f1-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf4f1-108">Requirements</span></span>  

 <span data-ttu-id="bf4f1-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf4f1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf4f1-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bf4f1-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf4f1-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bf4f1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf4f1-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf4f1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
