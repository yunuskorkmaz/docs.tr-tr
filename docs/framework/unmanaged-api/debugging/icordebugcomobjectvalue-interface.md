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
ms.openlocfilehash: 4ff5c0d470e6eb84eb8b526f5e8f74e5e1a8118a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125481"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="b2a53-102">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2a53-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="b2a53-103">Bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) ile ilişkili bilgileri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2a53-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2a53-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b2a53-104">Methods</span></span>  
  
|<span data-ttu-id="b2a53-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b2a53-105">Method</span></span>|<span data-ttu-id="b2a53-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2a53-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2a53-107">GetCachedInterfacePointers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2a53-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="b2a53-108">Geçerli RCW 'da önbelleğe alınan ham arabirim işaretçilerini alır.</span><span class="sxs-lookup"><span data-stu-id="b2a53-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="b2a53-109">GetCachedInterfaceTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2a53-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="b2a53-110">Geçerli nesnenin küçük harf olarak kullanıldığı veya kullanıldığı arabirim türleri için bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2a53-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2a53-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2a53-111">Remarks</span></span>  
 <span data-ttu-id="b2a53-112">Bir "ICorDebugValue" arabiriminin bir örneğinin bir RCW 'yu temsil ettiğini denetlemek için, hata ayıklayıcı `IID_ICorDebugComObjectValue`"ICorDebugValue" üzerinde `QueryInterface` çağırır.</span><span class="sxs-lookup"><span data-stu-id="b2a53-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2a53-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2a53-113">Requirements</span></span>  
 <span data-ttu-id="b2a53-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2a53-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2a53-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b2a53-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2a53-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b2a53-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2a53-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2a53-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a53-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2a53-118">See also</span></span>

- [<span data-ttu-id="b2a53-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b2a53-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b2a53-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b2a53-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
