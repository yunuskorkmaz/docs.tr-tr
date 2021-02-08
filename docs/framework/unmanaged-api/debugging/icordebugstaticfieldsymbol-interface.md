---
description: ': ICorDebugStaticFieldSymbol arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugStaticFieldSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: 3aa9c98cef4cdc7edc519b06b6cf9b4b2192b4e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794682"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="e53b4-103">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e53b4-103">ICorDebugStaticFieldSymbol Interface</span></span>

<span data-ttu-id="e53b4-104">Statik bir alan için hata ayıklama simgesi bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e53b4-104">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e53b4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e53b4-105">Methods</span></span>  
  
|<span data-ttu-id="e53b4-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e53b4-106">Method</span></span>|<span data-ttu-id="e53b4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e53b4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e53b4-108">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e53b4-108">GetAddress Method</span></span>](icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="e53b4-109">Statik alanın adresini alır.</span><span class="sxs-lookup"><span data-stu-id="e53b4-109">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="e53b4-110">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e53b4-110">GetName Method</span></span>](icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="e53b4-111">Statik alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="e53b4-111">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="e53b4-112">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e53b4-112">GetSize Method</span></span>](icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="e53b4-113">Statik alanın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="e53b4-113">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e53b4-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e53b4-114">Remarks</span></span>  

 <span data-ttu-id="e53b4-115">`ICorDebugStaticFieldSymbol`Arabirim, bir statik alana yönelik hata ayıklama simgesi bilgilerini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e53b4-115">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e53b4-116">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e53b4-116">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e53b4-117">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="e53b4-117">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e53b4-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e53b4-118">Requirements</span></span>  

 <span data-ttu-id="e53b4-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e53b4-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e53b4-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e53b4-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e53b4-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e53b4-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e53b4-122">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e53b4-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e53b4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e53b4-123">See also</span></span>

- [<span data-ttu-id="e53b4-124">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e53b4-124">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="e53b4-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e53b4-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e53b4-126">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e53b4-126">Debugging</span></span>](index.md)
