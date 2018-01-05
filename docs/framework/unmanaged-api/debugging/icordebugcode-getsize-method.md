---
title: ICorDebugCode::GetSize Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.GetSize
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69c28cba90c8ebef1b178263c8edac2cb5914c0f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="f7155-102">ICorDebugCode::GetSize Metodu</span><span class="sxs-lookup"><span data-stu-id="f7155-102">ICorDebugCode::GetSize Method</span></span>
<span data-ttu-id="f7155-103">Bu "Icordebugcode" temsil ikili kod bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="f7155-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7155-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7155-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32    *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7155-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f7155-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="f7155-106">[out] İkili dosya bayt cinsinden boyutu gösteren bir işaretçi Bu kod `ICorDebugCode` nesne temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f7155-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7155-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7155-107">Requirements</span></span>  
 <span data-ttu-id="f7155-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7155-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7155-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7155-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7155-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7155-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7155-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7155-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7155-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f7155-112">See Also</span></span>  
 
