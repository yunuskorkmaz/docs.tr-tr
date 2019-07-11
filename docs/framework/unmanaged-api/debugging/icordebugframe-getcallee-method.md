---
title: ICorDebugFrame::GetCallee Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10a5247632f242a4b4e0d33cf7fa7233d1b1e13b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754207"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="e3300-102">ICorDebugFrame::GetCallee Metodu</span><span class="sxs-lookup"><span data-stu-id="e3300-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="e3300-103">Bir işaretçi olarak adlandırılan bu çerçeveyi geçerli zincirinde Icordebugframe nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="e3300-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3300-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3300-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3300-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e3300-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="e3300-106">[out] Adresine bir işaretçi bir `ICorDebugFrame` çağrılan çerçeveyi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="e3300-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="e3300-107">Bu değer arama çerçeveyi geçerli zincirindeki en içteki çerçeve ise null olur.</span><span class="sxs-lookup"><span data-stu-id="e3300-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3300-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3300-108">Requirements</span></span>  
 <span data-ttu-id="e3300-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3300-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3300-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3300-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3300-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3300-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3300-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3300-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
