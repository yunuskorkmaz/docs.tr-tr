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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd09ce27c0fea9dca8fd86afc563651d68542e13
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173153"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="78999-102">ICorDebug::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78999-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="78999-103">Başlatır `ICorDebug` nesne.</span><span class="sxs-lookup"><span data-stu-id="78999-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78999-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78999-104">Syntax</span></span>  
  
```  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="78999-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78999-105">Remarks</span></span>  
 <span data-ttu-id="78999-106">Hata ayıklayıcı çağırmalıdır `Initialize` oluşturma sırasında hata ayıklamayı başlatmak için zaman Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="78999-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="78999-107">Bu yöntem, önce başka bir yöntem üzerinde çağrılmalıdır `ICorDebug` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="78999-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78999-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78999-108">Requirements</span></span>  
 <span data-ttu-id="78999-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78999-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78999-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78999-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78999-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78999-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78999-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78999-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78999-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78999-113">See also</span></span>

- [<span data-ttu-id="78999-114">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78999-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
