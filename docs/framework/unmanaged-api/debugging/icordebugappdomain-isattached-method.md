---
title: "ICorDebugAppDomain::IsAttached Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.IsAttached
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a1af550de7198041a885a788d6b36349c8e1c091
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="2a193-102">ICorDebugAppDomain::IsAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a193-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="2a193-103">Hata ayıklayıcı uygulama etki alanına bağlı olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="2a193-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a193-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a193-104">Syntax</span></span>  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a193-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a193-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="2a193-106">[out] `true` hata ayıklayıcısı ekli uygulama etki alanı için; Aksi takdirde ise `false`.</span><span class="sxs-lookup"><span data-stu-id="2a193-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a193-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a193-107">Remarks</span></span>  
 <span data-ttu-id="2a193-108">Hata ayıklayıcı uygulama etki alanına ekler kadar Icordebugcontroller yöntemleri kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2a193-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a193-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a193-109">Requirements</span></span>  
 <span data-ttu-id="2a193-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a193-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a193-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a193-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a193-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a193-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a193-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a193-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
