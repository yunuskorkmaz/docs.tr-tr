---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugEval2:: NewStringWithLength yöntemi'
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
ms.openlocfilehash: 23864dabefcb4fc12f73c66bc2d19a6cca1aacf0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693531"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="a3d12-103">ICorDebugEval2::NewStringWithLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3d12-103">ICorDebugEval2::NewStringWithLength Method</span></span>

<span data-ttu-id="a3d12-104">Belirtilen bir uzunluğa sahip, belirtilen içeriğe sahip bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a3d12-104">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3d12-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3d12-105">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3d12-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3d12-106">Parameters</span></span>  

 `string`  
 <span data-ttu-id="a3d12-107">'ndaki Dize değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a3d12-107">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="a3d12-108">'ndaki Dizenin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="a3d12-108">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3d12-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3d12-109">Remarks</span></span>  

 <span data-ttu-id="a3d12-110">Dizenin sondaki NULL karakterinin yönetilen dizede olması bekleniyorsa, `NewStringWithLength` yöntemi çağıranın dize uzunluğunun sondaki null karakteri içerdiğinden emin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3d12-110">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="a3d12-111">Dize her zaman iş parçacığının yürütüldüğü uygulama etki alanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a3d12-111">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3d12-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3d12-112">Requirements</span></span>  

 <span data-ttu-id="a3d12-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3d12-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3d12-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a3d12-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3d12-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a3d12-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3d12-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3d12-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
