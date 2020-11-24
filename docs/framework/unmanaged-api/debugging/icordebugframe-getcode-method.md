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
ms.openlocfilehash: 29dc87bf465fc9751b5af795f7640b095e535e63
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690401"
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="9478b-102">ICorDebugFrame::GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9478b-102">ICorDebugFrame::GetCode Method</span></span>

<span data-ttu-id="9478b-103">Bu yığın çerçevesiyle ilişkili koda yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="9478b-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9478b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9478b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9478b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9478b-105">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="9478b-106">dışı Bu kareyle ilişkili kodu temsil eden bir ICorDebugCode nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9478b-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9478b-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9478b-107">Requirements</span></span>  

 <span data-ttu-id="9478b-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9478b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9478b-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9478b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9478b-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9478b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9478b-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9478b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
