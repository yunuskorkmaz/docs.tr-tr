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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ee602c85a2f591365d40984184780f70e8532bf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762706"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="a5e4d-102">ICorDebugModule::GetAssembly Metodu</span><span class="sxs-lookup"><span data-stu-id="a5e4d-102">ICorDebugModule::GetAssembly Method</span></span>
<span data-ttu-id="a5e4d-103">Bu modül için derlemeyi içeren alır.</span><span class="sxs-lookup"><span data-stu-id="a5e4d-103">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5e4d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5e4d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5e4d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5e4d-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="a5e4d-106">[out] Bu modül içeren derlemenin temsil eden bir Icordebugassembly nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a5e4d-106">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5e4d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5e4d-107">Requirements</span></span>  
 <span data-ttu-id="a5e4d-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5e4d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5e4d-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5e4d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5e4d-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5e4d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5e4d-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5e4d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
