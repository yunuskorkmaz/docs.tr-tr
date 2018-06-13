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
ms.openlocfilehash: f0412089fee27e556c2f9230e9b34de3391b9bd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402567"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="1ae16-102">ICorDebugAppDomain::IsAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ae16-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="1ae16-103">Hata ayıklayıcı uygulama etki alanına bağlı olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="1ae16-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ae16-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ae16-104">Syntax</span></span>  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ae16-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ae16-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="1ae16-106">[out] `true` hata ayıklayıcısı ekli uygulama etki alanı için; Aksi takdirde ise `false`.</span><span class="sxs-lookup"><span data-stu-id="1ae16-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ae16-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ae16-107">Remarks</span></span>  
 <span data-ttu-id="1ae16-108">Hata ayıklayıcı uygulama etki alanına ekler kadar Icordebugcontroller yöntemleri kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1ae16-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ae16-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ae16-109">Requirements</span></span>  
 <span data-ttu-id="1ae16-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ae16-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ae16-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ae16-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ae16-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ae16-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ae16-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ae16-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
