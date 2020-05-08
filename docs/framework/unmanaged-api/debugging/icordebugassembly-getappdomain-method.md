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
ms.openlocfilehash: 81936052c3fa2ad4fb77b503341b8b4873b80695
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894942"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="fd873-102">ICorDebugAssembly::GetAppDomain Metodu</span><span class="sxs-lookup"><span data-stu-id="fd873-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="fd873-103">Bu `ICorDebugAssembly` örneği içeren uygulama etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="fd873-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd873-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd873-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd873-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd873-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="fd873-106">dışı Uygulama etki alanını temsil eden ICorDebugAppDomain arabiriminin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fd873-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd873-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd873-107">Remarks</span></span>  
 <span data-ttu-id="fd873-108">Bu derleme sistem bütünleştirilmiş kodu ise null `GetAppDomain` değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="fd873-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd873-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd873-109">Requirements</span></span>  
 <span data-ttu-id="fd873-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd873-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd873-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fd873-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd873-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fd873-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd873-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd873-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
