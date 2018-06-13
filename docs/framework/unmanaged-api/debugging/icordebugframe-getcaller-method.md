---
title: ICorDebugFrame::GetCaller Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2452f4be0acde300676bf56011416e0a9ef16464
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411722"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="c6ff6-102">ICorDebugFrame::GetCaller Metodu</span><span class="sxs-lookup"><span data-stu-id="c6ff6-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="c6ff6-103">Bir işaretçi olarak adlandırılan bu çerçeve geçerli zincirinde Icordebugframe nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="c6ff6-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6ff6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6ff6-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6ff6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6ff6-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="c6ff6-106">[out] Adresine bir işaretçi bir `ICorDebugFrame` arama çerçeveyi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="c6ff6-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="c6ff6-107">Bu değer çağrılan çerçeve geçerli zincirindeki en dıştaki çerçeve ise null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c6ff6-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6ff6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6ff6-108">Requirements</span></span>  
 <span data-ttu-id="c6ff6-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6ff6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6ff6-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6ff6-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6ff6-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6ff6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6ff6-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6ff6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
