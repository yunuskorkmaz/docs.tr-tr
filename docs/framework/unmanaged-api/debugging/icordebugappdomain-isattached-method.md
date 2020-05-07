---
title: ICorDebugAppDomain::IsAttached Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.IsAttached
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type:
- apiref
ms.openlocfilehash: a2f6df7647ffe9f2adff963b6629ed29ece053c0
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895159"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="49c0f-102">ICorDebugAppDomain::IsAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="49c0f-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="49c0f-103">Hata ayıklayıcının uygulama etki alanına bağlı olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="49c0f-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49c0f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49c0f-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49c0f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="49c0f-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="49c0f-106">dışı `true` hata ayıklayıcı uygulama etki alanına eklenmişse; Aksi takdirde `false`,.</span><span class="sxs-lookup"><span data-stu-id="49c0f-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49c0f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49c0f-107">Remarks</span></span>  
 <span data-ttu-id="49c0f-108">ICorDebugController yöntemleri, hata ayıklayıcı uygulama etki alanına iliştirene kadar kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="49c0f-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49c0f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49c0f-109">Requirements</span></span>  
 <span data-ttu-id="49c0f-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49c0f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49c0f-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="49c0f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49c0f-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="49c0f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49c0f-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49c0f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
