---
title: ICorDebugFrame::GetFunction Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d3bd671d90ff924bce32b6d67c33b90b4fa042f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="44481-102">ICorDebugFrame::GetFunction Metodu</span><span class="sxs-lookup"><span data-stu-id="44481-102">ICorDebugFrame::GetFunction Method</span></span>
<span data-ttu-id="44481-103">Bu yığın çerçevesi ile ilişkili kodunu içerir işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="44481-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44481-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44481-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44481-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="44481-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="44481-106">[out] Bir işaretçi adresine ICorDebugFunction nesnenin Bu yığın çerçevesi ile ilişkili kodunu içeren işlevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="44481-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44481-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44481-107">Remarks</span></span>  
 <span data-ttu-id="44481-108">`GetFunction` Yöntemi çerçeve herhangi belirli bir işlev ile ilişkili değilse başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="44481-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44481-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44481-109">Requirements</span></span>  
 <span data-ttu-id="44481-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44481-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44481-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44481-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44481-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44481-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44481-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44481-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
