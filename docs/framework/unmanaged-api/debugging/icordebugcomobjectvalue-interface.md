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
ms.openlocfilehash: ed5b39ed4b2a14c071bf23fb04efbad6834e8a9d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783965"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="baa97-102">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="baa97-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="baa97-103">Bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) ile ilişkili bilgileri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="baa97-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="baa97-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="baa97-104">Methods</span></span>  
  
|<span data-ttu-id="baa97-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="baa97-105">Method</span></span>|<span data-ttu-id="baa97-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="baa97-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="baa97-107">GetCachedInterfacePointers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="baa97-107">GetCachedInterfacePointers Method</span></span>](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="baa97-108">Geçerli RCW 'da önbelleğe alınan ham arabirim işaretçilerini alır.</span><span class="sxs-lookup"><span data-stu-id="baa97-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="baa97-109">GetCachedInterfaceTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="baa97-109">GetCachedInterfaceTypes Method</span></span>](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="baa97-110">Geçerli nesnenin küçük harf olarak kullanıldığı veya kullanıldığı arabirim türleri için bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="baa97-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baa97-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="baa97-111">Remarks</span></span>  
 <span data-ttu-id="baa97-112">Bir "ICorDebugValue" arabiriminin bir örneğinin bir RCW 'yu temsil ettiğini denetlemek için, hata ayıklayıcı `IID_ICorDebugComObjectValue`"ICorDebugValue" üzerinde `QueryInterface` çağırır.</span><span class="sxs-lookup"><span data-stu-id="baa97-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baa97-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="baa97-113">Requirements</span></span>  
 <span data-ttu-id="baa97-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baa97-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baa97-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="baa97-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="baa97-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="baa97-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="baa97-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baa97-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baa97-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="baa97-118">See also</span></span>

- [<span data-ttu-id="baa97-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="baa97-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="baa97-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="baa97-120">Debugging</span></span>](index.md)
