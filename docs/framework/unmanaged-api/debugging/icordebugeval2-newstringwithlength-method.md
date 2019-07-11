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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a90f0a0319d88654d0310530749ef35b7095e0fb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754433"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="0832a-102">ICorDebugEval2::NewStringWithLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0832a-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="0832a-103">Belirtilen içerikle belirtilen uzunlukta bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0832a-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0832a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0832a-104">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0832a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0832a-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="0832a-106">[in] Dize değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0832a-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="0832a-107">[in] Dize uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="0832a-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0832a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0832a-108">Remarks</span></span>  
 <span data-ttu-id="0832a-109">Dize sondaki, null karakteri yönetilen dizesinde çağıran olması bekleniyorsa `NewStringWithLength` yöntemi dize uzunluğu sondaki null karakter içerdiğinden emin gerekir.</span><span class="sxs-lookup"><span data-stu-id="0832a-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="0832a-110">Dize, her zaman iş parçacığı gerçekleştirmektedir uygulama etki alanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0832a-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0832a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0832a-111">Requirements</span></span>  
 <span data-ttu-id="0832a-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0832a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0832a-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0832a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0832a-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0832a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0832a-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0832a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
