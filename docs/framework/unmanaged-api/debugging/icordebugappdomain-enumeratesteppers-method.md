---
description: ': ICorDebugAppDomain:: Enumeratestepmanagermethod hakkında daha fazla bilgi edinin'
title: ICorDebugAppDomain::EnumerateSteppers Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateSteppers
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateSteppers
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateSteppers method [.NET Framework debugging]
- EnumerateSteppers method [.NET Framework debugging]
ms.assetid: 3f3c4503-570e-44c1-ae6a-a3c6b840c732
topic_type:
- apiref
ms.openlocfilehash: a9c7f8b1486522b4740ec18c575c9876512b7d8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754257"
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="1ae62-103">ICorDebugAppDomain::EnumerateSteppers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ae62-103">ICorDebugAppDomain::EnumerateSteppers Method</span></span>

<span data-ttu-id="1ae62-104">Uygulama etki alanındaki tüm etkin stepdenetleyicileri için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="1ae62-104">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ae62-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ae62-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ae62-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ae62-106">Parameters</span></span>  

 `ppSteppers`  
 <span data-ttu-id="1ae62-107">dışı Uygulama etki alanındaki tüm etkin stepdenetleyicileri için numaralandırıcı olan ICorDebugStepperEnum nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1ae62-107">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ae62-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ae62-108">Requirements</span></span>  

 <span data-ttu-id="1ae62-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ae62-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ae62-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1ae62-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ae62-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1ae62-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ae62-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ae62-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
