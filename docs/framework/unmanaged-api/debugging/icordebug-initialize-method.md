---
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
ms.openlocfilehash: 5cdd89ebdbb5abb9b001c1489a54bfb867808c5c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723434"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="2f878-102">ICorDebug::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f878-102">ICorDebug::Initialize Method</span></span>

<span data-ttu-id="2f878-103">Nesnesini başlatır `ICorDebug` .</span><span class="sxs-lookup"><span data-stu-id="2f878-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f878-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2f878-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2f878-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f878-105">Remarks</span></span>  

 <span data-ttu-id="2f878-106">Hata ayıklayıcı, `Initialize` hata ayıklama hizmetlerini başlatmak için oluşturma zamanında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2f878-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="2f878-107">Bu yöntem, üzerinde başka herhangi bir yöntem çağrılmadan önce çağrılmalıdır `ICorDebug` .</span><span class="sxs-lookup"><span data-stu-id="2f878-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f878-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f878-108">Requirements</span></span>  

 <span data-ttu-id="2f878-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f878-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f878-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2f878-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f878-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2f878-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f878-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f878-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f878-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f878-113">See also</span></span>

- [<span data-ttu-id="2f878-114">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f878-114">ICorDebug Interface</span></span>](icordebug-interface.md)
