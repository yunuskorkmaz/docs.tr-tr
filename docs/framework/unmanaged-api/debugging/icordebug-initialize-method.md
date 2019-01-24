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
ms.openlocfilehash: f7b4cf6c50d624f82a75f19b8e3f42c73910c4e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709305"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="b551e-102">ICorDebug::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b551e-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="b551e-103">Başlatır `ICorDebug` nesne.</span><span class="sxs-lookup"><span data-stu-id="b551e-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b551e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b551e-104">Syntax</span></span>  
  
```  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b551e-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b551e-105">Remarks</span></span>  
 <span data-ttu-id="b551e-106">Hata ayıklayıcı çağırmalıdır `Initialize` oluşturma sırasında hata ayıklamayı başlatmak için zaman Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="b551e-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="b551e-107">Bu yöntem, önce başka bir yöntem üzerinde çağrılmalıdır `ICorDebug` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b551e-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b551e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b551e-108">Requirements</span></span>  
 <span data-ttu-id="b551e-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b551e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b551e-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b551e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b551e-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b551e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b551e-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b551e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b551e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b551e-113">See also</span></span>
- [<span data-ttu-id="b551e-114">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b551e-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
