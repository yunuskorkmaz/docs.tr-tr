---
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
ms.openlocfilehash: ae0c23e3d48df6add8951a6d90029185a99bb323
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128839"
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="c1a77-102">ICorDebugProcess::GetID Metodu</span><span class="sxs-lookup"><span data-stu-id="c1a77-102">ICorDebugProcess::GetID Method</span></span>
<span data-ttu-id="c1a77-103">İşlemin işletim sistemi (OS) KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="c1a77-103">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1a77-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1a77-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1a77-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1a77-105">Parameters</span></span>  
 `pdwProcessId`  
 <span data-ttu-id="c1a77-106">dışı İşlemin benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="c1a77-106">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1a77-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1a77-107">Requirements</span></span>  
 <span data-ttu-id="c1a77-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1a77-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1a77-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c1a77-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1a77-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c1a77-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1a77-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1a77-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
