---
title: "ICorDebugChain::EnumerateFrames Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.EnumerateFrames
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d9df99c239568948c04f61ca4ec5e2b9207930f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="19ee6-102">ICorDebugChain::EnumerateFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19ee6-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="19ee6-103">En son çerçeve ile başlayarak zincirde tüm yönetilen yığın çerçeveleri içeren bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="19ee6-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19ee6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19ee6-104">Syntax</span></span>  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19ee6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="19ee6-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="19ee6-106">[out] Yığın çerçeveleri Numaralandırıcı bir Icordebugframeenum nesne adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="19ee6-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19ee6-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19ee6-107">Remarks</span></span>  
 <span data-ttu-id="19ee6-108">Zincir iş parçacığı için fiziksel çağrı yığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="19ee6-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="19ee6-109">`EnumerateFrames` Yöntemi için yalnızca yönetilen zincirleri adlı.</span><span class="sxs-lookup"><span data-stu-id="19ee6-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="19ee6-110">Hata ayıklama API'si yönetilmeyen zincirde yer alan çerçeveler edinme yöntemleri sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="19ee6-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="19ee6-111">Hata ayıklayıcı bu bilgileri almak için başka yöntemler kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="19ee6-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19ee6-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19ee6-112">Requirements</span></span>  
 <span data-ttu-id="19ee6-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19ee6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19ee6-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19ee6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19ee6-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19ee6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19ee6-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19ee6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
