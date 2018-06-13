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
ms.openlocfilehash: 11afee9c2a84999ccad2cdc12e2a14a4dc17d542
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412532"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="9fa6c-102">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9fa6c-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="9fa6c-103">Bir çalışma zamanı aranabilir sarmalayıcısı (RCW) ile ilgili bilgileri almak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fa6c-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9fa6c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9fa6c-104">Methods</span></span>  
  
|<span data-ttu-id="9fa6c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9fa6c-105">Method</span></span>|<span data-ttu-id="9fa6c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9fa6c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9fa6c-107">GetCachedInterfacePointers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9fa6c-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="9fa6c-108">Üzerinde geçerli RCW önbelleğe ham arabirim işaretçileri alır.</span><span class="sxs-lookup"><span data-stu-id="9fa6c-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="9fa6c-109">GetCachedInterfaceTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9fa6c-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="9fa6c-110">Bir numaralandırıcı arabirimi türleri için geçerli nesne için ortası veya bırakıldığı olarak kullanılan olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fa6c-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fa6c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9fa6c-111">Remarks</span></span>  
 <span data-ttu-id="9fa6c-112">"ICorDebugValue" arabiriminin bir örneği bir RCW temsil edip etmediğini denetlemek için bir hata ayıklayıcısı çağırır `QueryInterface` ile "Icordebugvalue" üzerinde `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="9fa6c-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fa6c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9fa6c-113">Requirements</span></span>  
 <span data-ttu-id="9fa6c-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fa6c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fa6c-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9fa6c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fa6c-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fa6c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fa6c-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fa6c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa6c-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fa6c-118">See Also</span></span>  
 [<span data-ttu-id="9fa6c-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9fa6c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9fa6c-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9fa6c-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
