---
title: ICorDebugModule::GetAssembly Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetAssembly
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetAssembly
helpviewer_keywords:
- ICorDebugModule::GetAssembly method [.NET Framework debugging]
- GetAssembly method [.NET Framework debugging]
ms.assetid: 989762c4-3d15-4485-b8ee-69e0fa8ec895
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 98d4670fc1d571d2a959b2a69ea8619bd8b40007
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="be379-102">ICorDebugModule::GetAssembly Metodu</span><span class="sxs-lookup"><span data-stu-id="be379-102">ICorDebugModule::GetAssembly Method</span></span>
<span data-ttu-id="be379-103">Bu modül için içeren derleme alır.</span><span class="sxs-lookup"><span data-stu-id="be379-103">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be379-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be379-104">Syntax</span></span>  
  
```  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be379-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be379-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="be379-106">[out] Bu modül içeren derlemenin temsil eden bir Icordebugassembly nesnesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="be379-106">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be379-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be379-107">Requirements</span></span>  
 <span data-ttu-id="be379-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be379-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be379-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be379-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be379-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be379-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be379-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be379-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
