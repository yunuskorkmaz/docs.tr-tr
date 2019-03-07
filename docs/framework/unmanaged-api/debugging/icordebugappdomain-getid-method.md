---
title: ICorDebugAppDomain::GetId Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetId
helpviewer_keywords:
- GetId method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetId method [.NET Framework debugging]
ms.assetid: 32c27576-71fa-42ee-8230-67b92913ea08
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0aefc19ca0c255c9c8ea40fcc12fc5cba1b00f6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501466"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="6fd1f-102">ICorDebugAppDomain::GetId Metodu</span><span class="sxs-lookup"><span data-stu-id="6fd1f-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="6fd1f-103">Uygulama etki alanının benzersiz tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="6fd1f-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fd1f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6fd1f-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fd1f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6fd1f-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="6fd1f-106">[out] Uygulama etki alanının benzersiz tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6fd1f-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fd1f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6fd1f-107">Remarks</span></span>  
 <span data-ttu-id="6fd1f-108">Uygulama etki alanını içeren işlem içinde benzersiz tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="6fd1f-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fd1f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6fd1f-109">Requirements</span></span>  
 <span data-ttu-id="6fd1f-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fd1f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fd1f-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6fd1f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fd1f-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fd1f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fd1f-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fd1f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
