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
ms.openlocfilehash: 528db447df4d71d67441b05ad29e6a900c59afbb
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892818"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="5c1ea-102">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c1ea-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="5c1ea-103">Bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) ile ilişkili bilgileri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c1ea-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c1ea-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5c1ea-104">Methods</span></span>  
  
|<span data-ttu-id="5c1ea-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5c1ea-105">Method</span></span>|<span data-ttu-id="5c1ea-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c1ea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c1ea-107">GetCachedInterfacePointers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c1ea-107">GetCachedInterfacePointers Method</span></span>](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="5c1ea-108">Geçerli RCW 'da önbelleğe alınan ham arabirim işaretçilerini alır.</span><span class="sxs-lookup"><span data-stu-id="5c1ea-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="5c1ea-109">GetCachedInterfaceTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c1ea-109">GetCachedInterfaceTypes Method</span></span>](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="5c1ea-110">Geçerli nesnenin küçük harf olarak kullanıldığı veya kullanıldığı arabirim türleri için bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c1ea-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c1ea-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c1ea-111">Remarks</span></span>  
 <span data-ttu-id="5c1ea-112">"ICorDebugValue" arabiriminin bir örneğinin bir RCW 'yu temsil ettiğini denetlemek için, ile `QueryInterface` `IID_ICorDebugComObjectValue`"ICorDebugValue" üzerinde bir hata ayıklayıcı çağırır.</span><span class="sxs-lookup"><span data-stu-id="5c1ea-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c1ea-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c1ea-113">Requirements</span></span>  
 <span data-ttu-id="5c1ea-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c1ea-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c1ea-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5c1ea-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c1ea-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5c1ea-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c1ea-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c1ea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c1ea-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c1ea-118">See also</span></span>

- [<span data-ttu-id="5c1ea-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5c1ea-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5c1ea-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5c1ea-120">Debugging</span></span>](index.md)
