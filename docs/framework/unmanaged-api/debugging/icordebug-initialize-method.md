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
ms.openlocfilehash: 3d27cf1987d7e9896885f87857554f4039c8d714
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788988"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="1347a-102">ICorDebug::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1347a-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="1347a-103">`ICorDebug` nesnesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="1347a-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1347a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1347a-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1347a-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1347a-105">Remarks</span></span>  
 <span data-ttu-id="1347a-106">Hata ayıklayıcı, hata ayıklama hizmetlerini başlatmak için oluşturma sırasında `Initialize` çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1347a-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="1347a-107">Bu yöntem, `ICorDebug` diğer herhangi bir yöntem çağrılmadan önce çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1347a-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1347a-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1347a-108">Requirements</span></span>  
 <span data-ttu-id="1347a-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1347a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1347a-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1347a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1347a-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1347a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1347a-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1347a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1347a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1347a-113">See also</span></span>

- [<span data-ttu-id="1347a-114">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1347a-114">ICorDebug Interface</span></span>](icordebug-interface.md)
