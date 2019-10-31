---
title: ICorDebugInstanceFieldSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 2ed1d70f554ca0a4a49639fe53a2ddbb0497c0a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122728"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="f7d23-102">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7d23-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="f7d23-103">Bir örnek alanı için hata ayıklama simgesi bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f7d23-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f7d23-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f7d23-104">Methods</span></span>  
  
|<span data-ttu-id="f7d23-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f7d23-105">Method</span></span>|<span data-ttu-id="f7d23-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7d23-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f7d23-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7d23-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="f7d23-108">Örnek alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="f7d23-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="f7d23-109">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7d23-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="f7d23-110">Üst sınıfındaki bu örnek alanının bayt cinsinden konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="f7d23-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="f7d23-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7d23-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="f7d23-112">Örnek alanının bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="f7d23-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7d23-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7d23-113">Remarks</span></span>  
 <span data-ttu-id="f7d23-114">`ICorDebugInstanceFieldSymbol` arabirimi bir örnek alanı için hata ayıklama sembol bilgisini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f7d23-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7d23-115">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7d23-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f7d23-116">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="f7d23-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7d23-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7d23-117">Requirements</span></span>  
 <span data-ttu-id="f7d23-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7d23-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7d23-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f7d23-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7d23-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f7d23-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7d23-121">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7d23-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7d23-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7d23-122">See also</span></span>

- [<span data-ttu-id="f7d23-123">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7d23-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="f7d23-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f7d23-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f7d23-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f7d23-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
