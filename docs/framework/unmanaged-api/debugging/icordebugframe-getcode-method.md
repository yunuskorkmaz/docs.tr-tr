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
ms.openlocfilehash: c8914ba1090ec5fd6540e9ead302675cb44f37e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208609"
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="81dda-102">ICorDebugFrame::GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="81dda-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="81dda-103">Bu yığın çerçevesiyle ilişkili koda yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="81dda-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81dda-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81dda-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81dda-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81dda-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="81dda-106">dışı Bu kareyle ilişkili kodu temsil eden bir ICorDebugCode nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="81dda-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81dda-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81dda-107">Requirements</span></span>  
 <span data-ttu-id="81dda-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81dda-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81dda-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="81dda-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81dda-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="81dda-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81dda-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81dda-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
