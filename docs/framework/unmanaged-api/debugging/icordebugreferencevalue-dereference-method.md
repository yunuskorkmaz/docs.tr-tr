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
ms.openlocfilehash: 6bb2a6b68a3c6e981a2d6c833d3f44d4c836bd23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124005"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="fe5f9-102">ICorDebugReferenceValue::Dereference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe5f9-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="fe5f9-103">Başvurulan nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="fe5f9-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe5f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe5f9-104">Syntax</span></span>  
  
```cpp  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe5f9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe5f9-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="fe5f9-106">dışı Bu ICorDebugReferenceValue nesnesinin işaret ettiği nesneyi temsil eden ICorDebugValue 'ın adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fe5f9-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe5f9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe5f9-107">Remarks</span></span>  
 <span data-ttu-id="fe5f9-108">`ICorDebugValue` nesnesi yalnızca başvurusu henüz devre dışı bırakılmadıysa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fe5f9-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe5f9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe5f9-109">Requirements</span></span>  
 <span data-ttu-id="fe5f9-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe5f9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe5f9-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fe5f9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe5f9-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fe5f9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe5f9-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe5f9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
