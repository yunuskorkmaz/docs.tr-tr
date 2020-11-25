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
ms.openlocfilehash: 55a798bcc575aee3f309c35eb454a0675e0cbd97
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734095"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="97832-102">ICorDebugAssembly::GetAppDomain Metodu</span><span class="sxs-lookup"><span data-stu-id="97832-102">ICorDebugAssembly::GetAppDomain Method</span></span>

<span data-ttu-id="97832-103">Bu örneği içeren uygulama etki alanına bir arabirim işaretçisi alır `ICorDebugAssembly` .</span><span class="sxs-lookup"><span data-stu-id="97832-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97832-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="97832-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97832-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97832-105">Parameters</span></span>  

 `ppAppDomain`  
 <span data-ttu-id="97832-106">dışı Uygulama etki alanını temsil eden ICorDebugAppDomain arabiriminin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="97832-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97832-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97832-107">Remarks</span></span>  

 <span data-ttu-id="97832-108">Bu derleme sistem bütünleştirilmiş kodu ise `GetAppDomain` null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="97832-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97832-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97832-109">Requirements</span></span>  

 <span data-ttu-id="97832-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97832-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97832-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="97832-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97832-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="97832-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97832-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97832-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
