---
title: ICorDebugAssembly::EnumerateModules Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.EnumerateModules
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::EnumerateModules
helpviewer_keywords:
- ICorDebugAssembly::EnumerateModules method [.NET Framework debugging]
- EnumerateModules method [.NET Framework debugging]
ms.assetid: c7ba51a1-0dd5-4452-b471-232febe0f897
topic_type:
- apiref
ms.openlocfilehash: 12dc5466d5be73b327f171c389c41c55901f2915
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894951"
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="301ed-102">ICorDebugAssembly::EnumerateModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="301ed-102">ICorDebugAssembly::EnumerateModules Method</span></span>
<span data-ttu-id="301ed-103">İçinde yer alan modüller için bir Numaralandırıcı alır `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="301ed-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="301ed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="301ed-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="301ed-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="301ed-105">Parameters</span></span>  
 `ppModules`  
 <span data-ttu-id="301ed-106">dışı Numaralandırıcı olan ICorDebugModuleEnum arabiriminin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="301ed-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="301ed-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="301ed-107">Requirements</span></span>  
 <span data-ttu-id="301ed-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="301ed-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="301ed-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="301ed-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="301ed-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="301ed-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="301ed-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="301ed-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
