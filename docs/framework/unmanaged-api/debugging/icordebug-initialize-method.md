---
description: ': ICorDebug:: Initialize yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebug::Initialize Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.Initialize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type:
- apiref
ms.openlocfilehash: 6b6ddd8c1c21470477420909bcf75906b5731ee6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791601"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="32c2b-103">ICorDebug::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="32c2b-103">ICorDebug::Initialize Method</span></span>

<span data-ttu-id="32c2b-104">Nesnesini başlatır `ICorDebug` .</span><span class="sxs-lookup"><span data-stu-id="32c2b-104">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32c2b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="32c2b-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="32c2b-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32c2b-106">Remarks</span></span>  

 <span data-ttu-id="32c2b-107">Hata ayıklayıcı, `Initialize` hata ayıklama hizmetlerini başlatmak için oluşturma zamanında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="32c2b-107">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="32c2b-108">Bu yöntem, üzerinde başka herhangi bir yöntem çağrılmadan önce çağrılmalıdır `ICorDebug` .</span><span class="sxs-lookup"><span data-stu-id="32c2b-108">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32c2b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32c2b-109">Requirements</span></span>  

 <span data-ttu-id="32c2b-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32c2b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32c2b-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="32c2b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32c2b-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="32c2b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32c2b-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32c2b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32c2b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32c2b-114">See also</span></span>

- [<span data-ttu-id="32c2b-115">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32c2b-115">ICorDebug Interface</span></span>](icordebug-interface.md)
