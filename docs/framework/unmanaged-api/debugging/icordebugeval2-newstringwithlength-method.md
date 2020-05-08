---
title: ICorDebugEval2::NewStringWithLength Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
ms.openlocfilehash: a2b76cb59a95082e0cf9c0884b8277cca3c8fe8d
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976076"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="3ab60-102">ICorDebugEval2::NewStringWithLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ab60-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="3ab60-103">Belirtilen bir uzunluğa sahip, belirtilen içeriğe sahip bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3ab60-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ab60-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ab60-104">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ab60-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3ab60-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="3ab60-106">'ndaki Dize değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3ab60-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="3ab60-107">'ndaki Dizenin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="3ab60-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ab60-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ab60-108">Remarks</span></span>  
 <span data-ttu-id="3ab60-109">Dizenin sondaki NULL karakterinin yönetilen dizede olması bekleniyorsa, `NewStringWithLength` yöntemi çağıranın dize uzunluğunun sondaki null karakteri içerdiğinden emin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="3ab60-110">Dize her zaman iş parçacığının yürütüldüğü uygulama etki alanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3ab60-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ab60-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ab60-111">Requirements</span></span>  
 <span data-ttu-id="3ab60-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ab60-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ab60-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3ab60-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ab60-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3ab60-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ab60-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ab60-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
