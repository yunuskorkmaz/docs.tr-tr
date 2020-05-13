---
title: ICorDebugInstanceFieldSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 092f2a8acdffa9f91176bdf0ca10b8db9cff6d37
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209936"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="9f03c-102">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f03c-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="9f03c-103">Bir örnek alanı için hata ayıklama simgesi bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9f03c-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9f03c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9f03c-104">Methods</span></span>  
  
|<span data-ttu-id="9f03c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9f03c-105">Method</span></span>|<span data-ttu-id="9f03c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f03c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9f03c-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f03c-107">GetName Method</span></span>](icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="9f03c-108">Örnek alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="9f03c-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="9f03c-109">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f03c-109">GetOffset Method</span></span>](icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="9f03c-110">Üst sınıfındaki bu örnek alanının bayt cinsinden konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="9f03c-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="9f03c-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f03c-111">GetSize Method</span></span>](icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="9f03c-112">Örnek alanının bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="9f03c-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f03c-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f03c-113">Remarks</span></span>  
 <span data-ttu-id="9f03c-114">`ICorDebugInstanceFieldSymbol`Arabirim, bir örnek alanı için hata ayıklama sembol bilgisini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9f03c-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9f03c-115">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9f03c-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="9f03c-116">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="9f03c-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f03c-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f03c-117">Requirements</span></span>  
 <span data-ttu-id="9f03c-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f03c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f03c-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9f03c-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f03c-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9f03c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f03c-121">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f03c-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f03c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f03c-122">See also</span></span>

- [<span data-ttu-id="9f03c-123">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f03c-123">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="9f03c-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9f03c-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9f03c-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9f03c-125">Debugging</span></span>](index.md)
