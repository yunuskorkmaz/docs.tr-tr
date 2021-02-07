---
description: ': ICorDebugComObjectValue arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3c071c371ae6e330431630cfb1934b538d62efe6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710822"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="bd169-103">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd169-103">ICorDebugComObjectValue Interface</span></span>

<span data-ttu-id="bd169-104">Bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) ile ilişkili bilgileri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd169-104">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bd169-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bd169-105">Methods</span></span>  
  
|<span data-ttu-id="bd169-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bd169-106">Method</span></span>|<span data-ttu-id="bd169-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd169-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd169-108">GetCachedInterfacePointers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd169-108">GetCachedInterfacePointers Method</span></span>](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="bd169-109">Geçerli RCW 'da önbelleğe alınan ham arabirim işaretçilerini alır.</span><span class="sxs-lookup"><span data-stu-id="bd169-109">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="bd169-110">GetCachedInterfaceTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd169-110">GetCachedInterfaceTypes Method</span></span>](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="bd169-111">Geçerli nesnenin küçük harf olarak kullanıldığı veya kullanıldığı arabirim türleri için bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd169-111">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd169-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd169-112">Remarks</span></span>  

 <span data-ttu-id="bd169-113">"ICorDebugValue" arabiriminin bir örneğinin bir RCW 'yu temsil ettiğini denetlemek için, `QueryInterface` ile "ICorDebugValue" üzerinde bir hata ayıklayıcı çağırır `IID_ICorDebugComObjectValue` .</span><span class="sxs-lookup"><span data-stu-id="bd169-113">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd169-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd169-114">Requirements</span></span>  

 <span data-ttu-id="bd169-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd169-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd169-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bd169-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd169-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bd169-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd169-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd169-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd169-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd169-119">See also</span></span>

- [<span data-ttu-id="bd169-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bd169-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="bd169-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="bd169-121">Debugging</span></span>](index.md)
