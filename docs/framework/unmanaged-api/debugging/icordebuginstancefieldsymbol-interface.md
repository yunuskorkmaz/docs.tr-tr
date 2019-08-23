---
title: ICorDebugInstanceFieldSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e5f63df9354df6a4d142c2f6ae12f9a0d5600fb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910135"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="82164-102">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82164-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="82164-103">Bir örnek alanı için hata ayıklama simgesi bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="82164-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82164-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="82164-104">Methods</span></span>  
  
|<span data-ttu-id="82164-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="82164-105">Method</span></span>|<span data-ttu-id="82164-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82164-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82164-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82164-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="82164-108">Örnek alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="82164-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="82164-109">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82164-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="82164-110">Üst sınıfındaki bu örnek alanının bayt cinsinden konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="82164-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="82164-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82164-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="82164-112">Örnek alanının bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="82164-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82164-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82164-113">Remarks</span></span>  
 <span data-ttu-id="82164-114">`ICorDebugInstanceFieldSymbol` Arabirim, bir örnek alanı için hata ayıklama sembol bilgisini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="82164-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82164-115">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="82164-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="82164-116">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="82164-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82164-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82164-117">Requirements</span></span>  
 <span data-ttu-id="82164-118">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82164-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82164-119">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="82164-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82164-120">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="82164-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82164-121">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82164-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82164-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82164-122">See also</span></span>

- [<span data-ttu-id="82164-123">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82164-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="82164-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="82164-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="82164-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="82164-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
