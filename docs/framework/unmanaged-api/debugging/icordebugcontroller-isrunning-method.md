---
title: ICorDebugController::IsRunning Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.IsRunning
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4605b893169ccfc592aae0d07dc032f455314cc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412739"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="107cd-102">ICorDebugController::IsRunning Yöntemi</span><span class="sxs-lookup"><span data-stu-id="107cd-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="107cd-103">İşlemdeki iş parçacıklarının ücretsiz olarak çalışmakta olan olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="107cd-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="107cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="107cd-104">Syntax</span></span>  
  
```  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="107cd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="107cd-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="107cd-106">[out] Bir değer için bir işaretçi `true` serbestçe; Aksi halde, işlemdeki iş parçacıklarının çalıştırıyorsanız, `false`.</span><span class="sxs-lookup"><span data-stu-id="107cd-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="107cd-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="107cd-107">Requirements</span></span>  
 <span data-ttu-id="107cd-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="107cd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="107cd-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="107cd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="107cd-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="107cd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="107cd-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="107cd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="107cd-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="107cd-112">See Also</span></span>  
 
