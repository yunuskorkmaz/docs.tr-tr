---
description: ': ICorDebugAssembly:: GetAppDomain metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f67b2a211b080843e2bd7b8820a5bf54dae638e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712109"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="93f7b-103">ICorDebugAssembly::GetAppDomain Metodu</span><span class="sxs-lookup"><span data-stu-id="93f7b-103">ICorDebugAssembly::GetAppDomain Method</span></span>

<span data-ttu-id="93f7b-104">Bu örneği içeren uygulama etki alanına bir arabirim işaretçisi alır `ICorDebugAssembly` .</span><span class="sxs-lookup"><span data-stu-id="93f7b-104">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93f7b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93f7b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93f7b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93f7b-106">Parameters</span></span>  

 `ppAppDomain`  
 <span data-ttu-id="93f7b-107">dışı Uygulama etki alanını temsil eden ICorDebugAppDomain arabiriminin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="93f7b-107">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93f7b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93f7b-108">Remarks</span></span>  

 <span data-ttu-id="93f7b-109">Bu derleme sistem bütünleştirilmiş kodu ise `GetAppDomain` null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="93f7b-109">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93f7b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93f7b-110">Requirements</span></span>  

 <span data-ttu-id="93f7b-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93f7b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93f7b-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="93f7b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93f7b-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="93f7b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93f7b-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93f7b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
