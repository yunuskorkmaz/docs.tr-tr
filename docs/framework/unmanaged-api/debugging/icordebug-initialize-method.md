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
ms.openlocfilehash: aeecf19cb85ce5d7781c3dfedca079e97cab76ce
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895350"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="2d623-102">ICorDebug::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d623-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="2d623-103">`ICorDebug` Nesnesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="2d623-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d623-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d623-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2d623-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d623-105">Remarks</span></span>  
 <span data-ttu-id="2d623-106">Hata ayıklayıcı, hata `Initialize` ayıklama hizmetlerini başlatmak için oluşturma zamanında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2d623-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="2d623-107">Bu yöntem, üzerinde `ICorDebug` başka herhangi bir yöntem çağrılmadan önce çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2d623-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d623-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d623-108">Requirements</span></span>  
 <span data-ttu-id="2d623-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d623-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d623-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2d623-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d623-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2d623-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d623-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d623-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d623-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d623-113">See also</span></span>

- [<span data-ttu-id="2d623-114">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d623-114">ICorDebug Interface</span></span>](icordebug-interface.md)
