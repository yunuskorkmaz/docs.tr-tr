---
title: ICorDebugAssembly::GetAppDomain Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e22d112d1414b13033f73723821e5e4b5764e1c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401985"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="7c9f9-102">ICorDebugAssembly::GetAppDomain Metodu</span><span class="sxs-lookup"><span data-stu-id="7c9f9-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="7c9f9-103">Bu içeren uygulama etki alanı için bir arabirim işaretçisi alır `ICorDebugAssembly` örneği.</span><span class="sxs-lookup"><span data-stu-id="7c9f9-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c9f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c9f9-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c9f9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7c9f9-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="7c9f9-106">[out] Uygulama etki alanını temsil eden bir Icordebugappdomain arabirimi adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7c9f9-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c9f9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c9f9-107">Remarks</span></span>  
 <span data-ttu-id="7c9f9-108">Bu derleme sistem derlemesi ise `GetAppDomain` null döndürür.</span><span class="sxs-lookup"><span data-stu-id="7c9f9-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c9f9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c9f9-109">Requirements</span></span>  
 <span data-ttu-id="7c9f9-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c9f9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c9f9-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c9f9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c9f9-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c9f9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c9f9-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c9f9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
