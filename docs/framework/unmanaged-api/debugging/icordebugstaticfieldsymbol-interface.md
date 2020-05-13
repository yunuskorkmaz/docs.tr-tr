---
title: ICorDebugStaticFieldSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: f9b82f0f98a668555a8096d7575c049c31cae93a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379436"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="394a5-102">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="394a5-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="394a5-103">Statik bir alan için hata ayıklama simgesi bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="394a5-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="394a5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="394a5-104">Methods</span></span>  
  
|<span data-ttu-id="394a5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="394a5-105">Method</span></span>|<span data-ttu-id="394a5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="394a5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="394a5-107">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="394a5-107">GetAddress Method</span></span>](icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="394a5-108">Statik alanın adresini alır.</span><span class="sxs-lookup"><span data-stu-id="394a5-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="394a5-109">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="394a5-109">GetName Method</span></span>](icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="394a5-110">Statik alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="394a5-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="394a5-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="394a5-111">GetSize Method</span></span>](icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="394a5-112">Statik alanın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="394a5-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="394a5-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="394a5-113">Remarks</span></span>  
 <span data-ttu-id="394a5-114">`ICorDebugStaticFieldSymbol`Arabirim, bir statik alana yönelik hata ayıklama simgesi bilgilerini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="394a5-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="394a5-115">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="394a5-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="394a5-116">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="394a5-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="394a5-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="394a5-117">Requirements</span></span>  
 <span data-ttu-id="394a5-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="394a5-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="394a5-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="394a5-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="394a5-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="394a5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="394a5-121">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="394a5-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="394a5-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="394a5-122">See also</span></span>

- [<span data-ttu-id="394a5-123">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="394a5-123">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="394a5-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="394a5-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="394a5-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="394a5-125">Debugging</span></span>](index.md)
