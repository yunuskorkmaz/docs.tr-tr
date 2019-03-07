---
title: ICorDebugReferenceValue::Dereference Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b436fa14322d444a6c8b515ba8e50698eecb95ba
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487024"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="4cb31-102">ICorDebugReferenceValue::Dereference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4cb31-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="4cb31-103">Başvurulan nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="4cb31-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cb31-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cb31-104">Syntax</span></span>  
  
```  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cb31-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4cb31-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="4cb31-106">[out] Bu Icordebugreferencevalue nesneye işaret ettiği nesneyi temsil eden bir Icordebugvalue adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4cb31-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cb31-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4cb31-107">Remarks</span></span>  
 <span data-ttu-id="4cb31-108">`ICorDebugValue` Nesne, yalnızca kendi başvurusu değil henüz devre dışı durumdayken geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4cb31-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cb31-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4cb31-109">Requirements</span></span>  
 <span data-ttu-id="4cb31-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cb31-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cb31-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4cb31-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4cb31-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4cb31-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4cb31-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cb31-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
