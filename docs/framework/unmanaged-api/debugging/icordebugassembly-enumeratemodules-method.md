---
description: ': ICorDebugAssembly:: EnumerateModules Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5d34fb1762e8f953007d6fcb59ab1147028f06a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722873"
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="6e217-103">ICorDebugAssembly::EnumerateModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e217-103">ICorDebugAssembly::EnumerateModules Method</span></span>

<span data-ttu-id="6e217-104">İçinde yer alan modüller için bir Numaralandırıcı alır `ICorDebugAssembly` .</span><span class="sxs-lookup"><span data-stu-id="6e217-104">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e217-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e217-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e217-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e217-106">Parameters</span></span>  

 `ppModules`  
 <span data-ttu-id="6e217-107">dışı Numaralandırıcı olan ICorDebugModuleEnum arabiriminin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6e217-107">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e217-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e217-108">Requirements</span></span>  

 <span data-ttu-id="6e217-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e217-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e217-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6e217-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e217-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6e217-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e217-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e217-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
