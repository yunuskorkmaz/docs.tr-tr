---
title: ICorDebugEval::NewString Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
ms.openlocfilehash: b263fed7db5cb2ef687da45f8cbc99a02e1e3ea2
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976141"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="4bc99-102">ICorDebugEval::NewString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bc99-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="4bc99-103">Belirtilen içeriğe sahip yeni bir dize örneği ayırır.</span><span class="sxs-lookup"><span data-stu-id="4bc99-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bc99-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4bc99-104">Syntax</span></span>  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bc99-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4bc99-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="4bc99-106">'ndaki Dize için içerik işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4bc99-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bc99-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4bc99-107">Remarks</span></span>  
 <span data-ttu-id="4bc99-108">Dize her zaman iş parçacığının yürütüldüğü uygulama etki alanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4bc99-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bc99-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4bc99-109">Requirements</span></span>  
 <span data-ttu-id="4bc99-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bc99-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bc99-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4bc99-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4bc99-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4bc99-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bc99-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bc99-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
