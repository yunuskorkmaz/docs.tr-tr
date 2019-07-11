---
title: ICorDebugFrame::GetCode Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca64e392b930ed57691f05ae771bbaf305df8eb3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754067"
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="e9eb8-102">ICorDebugFrame::GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9eb8-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="e9eb8-103">Bu yığın çerçevesiyle ilgili koda bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="e9eb8-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9eb8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9eb8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9eb8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9eb8-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="e9eb8-106">[out] Bu çerçeve ile ilişkili kodunu temsil eden bir Icordebugcode nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e9eb8-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9eb8-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9eb8-107">Requirements</span></span>  
 <span data-ttu-id="e9eb8-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9eb8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9eb8-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9eb8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9eb8-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9eb8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9eb8-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9eb8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
