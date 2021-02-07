---
description: ': ICorDebugModule:: GetAssembly yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 88bda923cd4c3ebfa5da6b3343e1cead4cebbad9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722626"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="913ff-103">ICorDebugModule::GetAssembly Metodu</span><span class="sxs-lookup"><span data-stu-id="913ff-103">ICorDebugModule::GetAssembly Method</span></span>

<span data-ttu-id="913ff-104">Bu modülün kapsayan derlemesini alır.</span><span class="sxs-lookup"><span data-stu-id="913ff-104">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="913ff-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="913ff-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="913ff-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="913ff-106">Parameters</span></span>  

 `ppAssembly`  
 <span data-ttu-id="913ff-107">dışı Bu modülü içeren derlemeyi temsil eden ICorDebugAssembly nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="913ff-107">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="913ff-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="913ff-108">Requirements</span></span>  

 <span data-ttu-id="913ff-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="913ff-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="913ff-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="913ff-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="913ff-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="913ff-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="913ff-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="913ff-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
