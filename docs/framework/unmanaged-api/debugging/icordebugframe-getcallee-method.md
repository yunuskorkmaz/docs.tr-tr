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
ms.openlocfilehash: a179b68e2196eeadc712ae8f7d023b2943533335
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995858"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="71e73-102">ICorDebugFrame::GetCallee Metodu</span><span class="sxs-lookup"><span data-stu-id="71e73-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="71e73-103">Bir işaretçi olarak adlandırılan bu çerçeveyi geçerli zincirinde Icordebugframe nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="71e73-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71e73-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71e73-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71e73-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71e73-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="71e73-106">[out] Adresine bir işaretçi bir `ICorDebugFrame` çağrılan çerçeveyi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="71e73-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="71e73-107">Bu değer arama çerçeveyi geçerli zincirindeki en içteki çerçeve ise null olur.</span><span class="sxs-lookup"><span data-stu-id="71e73-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71e73-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71e73-108">Requirements</span></span>  
 <span data-ttu-id="71e73-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71e73-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71e73-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71e73-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71e73-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71e73-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71e73-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71e73-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
