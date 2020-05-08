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
ms.openlocfilehash: 63346c679efc083dea9ab0eaa4f983a5308695f8
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895249"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="66ffe-102">ICorDebugAppDomain::GetId Metodu</span><span class="sxs-lookup"><span data-stu-id="66ffe-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="66ffe-103">Uygulama etki alanının benzersiz tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="66ffe-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66ffe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66ffe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66ffe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66ffe-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="66ffe-106">dışı Uygulama etki alanının benzersiz tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="66ffe-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66ffe-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66ffe-107">Remarks</span></span>  
 <span data-ttu-id="66ffe-108">Uygulama etki alanı için tanımlayıcı, kapsayan işlem içinde benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="66ffe-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66ffe-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66ffe-109">Requirements</span></span>  
 <span data-ttu-id="66ffe-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66ffe-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66ffe-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="66ffe-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66ffe-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="66ffe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66ffe-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66ffe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
