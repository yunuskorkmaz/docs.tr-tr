---
title: ICorDebugProcess::GetID Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetID
helpviewer_keywords:
- GetID method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetID method [.NET Framework debugging]
ms.assetid: b0ba8453-fa7e-4c14-93e5-335409cd4a47
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d09888434048c312bd78dddf29d39a45f023695e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="32007-102">ICorDebugProcess::GetID Metodu</span><span class="sxs-lookup"><span data-stu-id="32007-102">ICorDebugProcess::GetID Method</span></span>
<span data-ttu-id="32007-103">İşlemin işletim sistemi (OS) Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="32007-103">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32007-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32007-104">Syntax</span></span>  
  
```  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32007-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32007-105">Parameters</span></span>  
 `pdwProcessId`  
 <span data-ttu-id="32007-106">[out] İşlemin benzersiz Kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="32007-106">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32007-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32007-107">Requirements</span></span>  
 <span data-ttu-id="32007-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32007-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32007-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32007-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32007-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32007-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32007-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32007-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
