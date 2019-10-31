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
ms.openlocfilehash: a5cda98cac0bc3fc6fb101fd0404b062224cb578
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134091"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="c42f6-102">ICorDebug::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c42f6-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="c42f6-103">`ICorDebug` nesnesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="c42f6-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c42f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c42f6-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c42f6-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c42f6-105">Remarks</span></span>  
 <span data-ttu-id="c42f6-106">Hata ayıklayıcı, hata ayıklama hizmetlerini başlatmak için oluşturma sırasında `Initialize` çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c42f6-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="c42f6-107">Bu yöntem, `ICorDebug` diğer herhangi bir yöntem çağrılmadan önce çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c42f6-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c42f6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c42f6-108">Requirements</span></span>  
 <span data-ttu-id="c42f6-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c42f6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c42f6-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c42f6-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c42f6-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c42f6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c42f6-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c42f6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c42f6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c42f6-113">See also</span></span>

- [<span data-ttu-id="c42f6-114">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c42f6-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
