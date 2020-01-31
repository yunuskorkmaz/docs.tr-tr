---
title: ICorDebugInstanceFieldSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 41258b0eeed5fbf8ab86546f74073f8eeaa3085c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777520"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="77403-102">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77403-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="77403-103">Bir örnek alanı için hata ayıklama simgesi bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="77403-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="77403-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="77403-104">Methods</span></span>  
  
|<span data-ttu-id="77403-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="77403-105">Method</span></span>|<span data-ttu-id="77403-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77403-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="77403-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77403-107">GetName Method</span></span>](icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="77403-108">Örnek alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="77403-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="77403-109">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77403-109">GetOffset Method</span></span>](icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="77403-110">Üst sınıfındaki bu örnek alanının bayt cinsinden konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="77403-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="77403-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77403-111">GetSize Method</span></span>](icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="77403-112">Örnek alanının bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="77403-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77403-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77403-113">Remarks</span></span>  
 <span data-ttu-id="77403-114">`ICorDebugInstanceFieldSymbol` arabirimi bir örnek alanı için hata ayıklama sembol bilgisini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77403-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77403-115">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="77403-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="77403-116">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="77403-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77403-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77403-117">Requirements</span></span>  
 <span data-ttu-id="77403-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77403-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77403-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="77403-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77403-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="77403-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77403-121">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77403-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77403-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77403-122">See also</span></span>

- [<span data-ttu-id="77403-123">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77403-123">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="77403-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="77403-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="77403-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="77403-125">Debugging</span></span>](index.md)
