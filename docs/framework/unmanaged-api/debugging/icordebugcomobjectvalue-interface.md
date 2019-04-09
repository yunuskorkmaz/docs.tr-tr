---
title: ICorDebugComObjectValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3387985ebf6027b9cd9dee372190da65939dbae3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098630"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="70dbe-102">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70dbe-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="70dbe-103">Bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) ile ilgili bilgileri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="70dbe-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70dbe-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="70dbe-104">Methods</span></span>  
  
|<span data-ttu-id="70dbe-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="70dbe-105">Method</span></span>|<span data-ttu-id="70dbe-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70dbe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70dbe-107">GetCachedInterfacePointers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70dbe-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="70dbe-108">Geçerli RCW üzerinde önbelleğe ham arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="70dbe-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="70dbe-109">GetCachedInterfaceTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70dbe-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="70dbe-110">Bir numaralandırıcı, geçerli nesne için büyük/küçük harfleri veya bırakıldığı olarak kullanılan, arabirim türlerinde sağlar.</span><span class="sxs-lookup"><span data-stu-id="70dbe-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70dbe-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70dbe-111">Remarks</span></span>  
 <span data-ttu-id="70dbe-112">"ICorDebugValue" arabiriminin bir örneği bir RCW temsil edip etmediğini denetlemek için bir hata ayıklayıcı çağırır `QueryInterface` ile "Icordebugvalue" üzerinde `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="70dbe-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70dbe-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70dbe-113">Requirements</span></span>  
 <span data-ttu-id="70dbe-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70dbe-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70dbe-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70dbe-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70dbe-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70dbe-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="70dbe-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="70dbe-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="70dbe-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70dbe-118">See also</span></span>

- [<span data-ttu-id="70dbe-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="70dbe-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="70dbe-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="70dbe-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
