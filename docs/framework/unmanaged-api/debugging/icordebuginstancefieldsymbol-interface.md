---
description: ': Icordebugınstancefieldsymbol arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugInstanceFieldSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: aa47c858ec5b4b0d04b851357fe81c0fc9b2e30a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791139"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="80f77-103">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80f77-103">ICorDebugInstanceFieldSymbol Interface</span></span>

<span data-ttu-id="80f77-104">Bir örnek alanı için hata ayıklama simgesi bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="80f77-104">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="80f77-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="80f77-105">Methods</span></span>  
  
|<span data-ttu-id="80f77-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="80f77-106">Method</span></span>|<span data-ttu-id="80f77-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80f77-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="80f77-108">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80f77-108">GetName Method</span></span>](icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="80f77-109">Örnek alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="80f77-109">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="80f77-110">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80f77-110">GetOffset Method</span></span>](icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="80f77-111">Üst sınıfındaki bu örnek alanının bayt cinsinden konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="80f77-111">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="80f77-112">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80f77-112">GetSize Method</span></span>](icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="80f77-113">Örnek alanının bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="80f77-113">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80f77-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80f77-114">Remarks</span></span>  

 <span data-ttu-id="80f77-115">`ICorDebugInstanceFieldSymbol`Arabirim, bir örnek alanı için hata ayıklama sembol bilgisini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="80f77-115">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80f77-116">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="80f77-116">This interface is available with .NET Native only.</span></span> <span data-ttu-id="80f77-117">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="80f77-117">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80f77-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80f77-118">Requirements</span></span>  

 <span data-ttu-id="80f77-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80f77-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80f77-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="80f77-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80f77-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="80f77-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80f77-122">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80f77-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80f77-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80f77-123">See also</span></span>

- [<span data-ttu-id="80f77-124">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80f77-124">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="80f77-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="80f77-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="80f77-126">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="80f77-126">Debugging</span></span>](index.md)
