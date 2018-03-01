---
title: ICorDebugFrame::GetCode Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a99b652a439a284033f3e7a9ecc46b3599fae00b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="c12f3-102">ICorDebugFrame::GetCode Metodu</span><span class="sxs-lookup"><span data-stu-id="c12f3-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="c12f3-103">Bir işaretçi Bu yığın çerçevesi ile ilişkili kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="c12f3-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c12f3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c12f3-104">Syntax</span></span>  
  
```  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c12f3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c12f3-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="c12f3-106">[out] Bir işaretçi adresine Icordebugcode nesnenin bu çerçeveyle ilişkili kodunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c12f3-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c12f3-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c12f3-107">Requirements</span></span>  
 <span data-ttu-id="c12f3-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c12f3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c12f3-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c12f3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c12f3-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c12f3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c12f3-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c12f3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
