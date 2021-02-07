---
description: ': ICorDebugProcess:: GetID Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugProcess::GetID Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetID
helpviewer_keywords:
- GetID method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetID method [.NET Framework debugging]
ms.assetid: b0ba8453-fa7e-4c14-93e5-335409cd4a47
topic_type:
- apiref
ms.openlocfilehash: 806e73724a88d08235f4a3e751f771abace1ad56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746990"
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="a5ec6-103">ICorDebugProcess::GetID Metodu</span><span class="sxs-lookup"><span data-stu-id="a5ec6-103">ICorDebugProcess::GetID Method</span></span>

<span data-ttu-id="a5ec6-104">İşlemin işletim sistemi (OS) KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="a5ec6-104">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5ec6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5ec6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5ec6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5ec6-106">Parameters</span></span>  

 `pdwProcessId`  
 <span data-ttu-id="a5ec6-107">dışı İşlemin benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a5ec6-107">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5ec6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5ec6-108">Requirements</span></span>  

 <span data-ttu-id="a5ec6-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5ec6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5ec6-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a5ec6-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5ec6-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a5ec6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5ec6-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5ec6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
