---
title: ICorDebugThread::GetActiveChain Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetActiveChain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f3f104933bc70682a531c0853cfc6eabcd357831
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="2c06c-102">ICorDebugThread::GetActiveChain Metodu</span><span class="sxs-lookup"><span data-stu-id="2c06c-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="2c06c-103">Arabirim işaretçisi etkin (en son) yığın zincire bu Icordebugthread nesnede alır.</span><span class="sxs-lookup"><span data-stu-id="2c06c-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c06c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c06c-104">Syntax</span></span>  
  
```  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c06c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c06c-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="2c06c-106">[out] Bir işaretçi adresine Icordebugchain nesnenin yığın zinciri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2c06c-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c06c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c06c-107">Remarks</span></span>  
 <span data-ttu-id="2c06c-108">`ppChain` Parametredir hiçbir yığın zinciri şu anda etkin değilse null.</span><span class="sxs-lookup"><span data-stu-id="2c06c-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c06c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c06c-109">Requirements</span></span>  
 <span data-ttu-id="2c06c-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c06c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c06c-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c06c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c06c-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c06c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c06c-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c06c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
