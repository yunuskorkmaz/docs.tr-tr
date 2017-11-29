---
title: ICorDebugFrame::GetCallee Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetCallee
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 54a26ad7d4818aae81b765ab4e6c0e5be821680e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="b4571-102">ICorDebugFrame::GetCallee Metodu</span><span class="sxs-lookup"><span data-stu-id="b4571-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="b4571-103">Bir işaretçi olarak adlandırılan bu çerçeve geçerli zincirinde Icordebugframe nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="b4571-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4571-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4571-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4571-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b4571-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="b4571-106">[out] Adresine bir işaretçi bir `ICorDebugFrame` çağrılan çerçeveyi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="b4571-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="b4571-107">Bu değer arama çerçeve geçerli zincirindeki en içteki çerçeve ise null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b4571-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4571-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4571-108">Requirements</span></span>  
 <span data-ttu-id="b4571-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4571-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4571-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4571-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4571-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4571-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4571-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4571-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
