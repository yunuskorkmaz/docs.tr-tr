---
title: ICorDebugModule::GetAssembly Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetAssembly
helpviewer_keywords:
- ICorDebugModule::GetAssembly method [.NET Framework debugging]
- GetAssembly method [.NET Framework debugging]
ms.assetid: 989762c4-3d15-4485-b8ee-69e0fa8ec895
topic_type:
- apiref
ms.openlocfilehash: e0ae11ee24a5e25fb439d5c502c4cda5bcb6a80e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710278"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="96765-102">ICorDebugModule::GetAssembly Metodu</span><span class="sxs-lookup"><span data-stu-id="96765-102">ICorDebugModule::GetAssembly Method</span></span>

<span data-ttu-id="96765-103">Bu modülün kapsayan derlemesini alır.</span><span class="sxs-lookup"><span data-stu-id="96765-103">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96765-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="96765-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96765-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96765-105">Parameters</span></span>  

 `ppAssembly`  
 <span data-ttu-id="96765-106">dışı Bu modülü içeren derlemeyi temsil eden ICorDebugAssembly nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="96765-106">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96765-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96765-107">Requirements</span></span>  

 <span data-ttu-id="96765-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96765-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96765-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="96765-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96765-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="96765-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96765-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96765-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
