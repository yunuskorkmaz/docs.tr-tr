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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa9576f568ef1f6da3eef812abb9674aa0d81dfb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996170"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="8f876-102">ICorDebugAppDomain::IsAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f876-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="8f876-103">Hata ayıklayıcı uygulama etki alanına bağlı olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="8f876-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f876-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f876-104">Syntax</span></span>  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f876-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f876-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="8f876-106">[out] `true` hata ayıklayıcı ise, uygulama etki alanına bağlı; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="8f876-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f876-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f876-107">Remarks</span></span>  
 <span data-ttu-id="8f876-108">Icordebugcontroller yöntemleri, hata ayıklayıcı uygulama etki alanına ekler kadar kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8f876-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f876-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f876-109">Requirements</span></span>  
 <span data-ttu-id="8f876-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f876-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f876-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f876-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f876-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f876-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f876-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f876-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
