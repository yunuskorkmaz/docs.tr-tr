---
title: ICorDebugFrame::GetFunction Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type:
- apiref
ms.openlocfilehash: 7bf73266f0269cfcd5371c5155856800036cc066
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209844"
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="0790b-102">ICorDebugFrame::GetFunction Metodu</span><span class="sxs-lookup"><span data-stu-id="0790b-102">ICorDebugFrame::GetFunction Method</span></span>
<span data-ttu-id="0790b-103">Bu yığın çerçevesiyle ilişkili kodu içeren işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="0790b-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0790b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0790b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0790b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0790b-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="0790b-106">dışı Bu yığın çerçevesiyle ilişkili kodu içeren işlevi temsil eden bir ICorDebugFunction nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0790b-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0790b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0790b-107">Remarks</span></span>  
 <span data-ttu-id="0790b-108">`GetFunction`Çerçeve belirli bir işlevle ilişkilendirilmediği takdirde yöntem başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="0790b-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0790b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0790b-109">Requirements</span></span>  
 <span data-ttu-id="0790b-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0790b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0790b-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0790b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0790b-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0790b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0790b-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0790b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
