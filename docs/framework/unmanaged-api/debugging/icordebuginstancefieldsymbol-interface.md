---
title: ICorDebugInstanceFieldSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 4ef0f7a46acf7e9df732d630c9eb22044e09d658
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724903"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="e1aa6-102">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1aa6-102">ICorDebugInstanceFieldSymbol Interface</span></span>

<span data-ttu-id="e1aa6-103">Bir örnek alanı için hata ayıklama simgesi bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e1aa6-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e1aa6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e1aa6-104">Methods</span></span>  
  
|<span data-ttu-id="e1aa6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e1aa6-105">Method</span></span>|<span data-ttu-id="e1aa6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1aa6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e1aa6-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1aa6-107">GetName Method</span></span>](icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="e1aa6-108">Örnek alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="e1aa6-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="e1aa6-109">GetOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="e1aa6-109">GetOffset Method</span></span>](icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="e1aa6-110">Üst sınıfındaki bu örnek alanının bayt cinsinden konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="e1aa6-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="e1aa6-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1aa6-111">GetSize Method</span></span>](icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="e1aa6-112">Örnek alanının bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="e1aa6-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1aa6-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1aa6-113">Remarks</span></span>  

 <span data-ttu-id="e1aa6-114">`ICorDebugInstanceFieldSymbol`Arabirim, bir örnek alanı için hata ayıklama sembol bilgisini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e1aa6-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1aa6-115">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1aa6-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e1aa6-116">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="e1aa6-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1aa6-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1aa6-117">Requirements</span></span>  

 <span data-ttu-id="e1aa6-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1aa6-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1aa6-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e1aa6-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1aa6-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e1aa6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1aa6-121">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1aa6-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1aa6-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1aa6-122">See also</span></span>

- [<span data-ttu-id="e1aa6-123">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1aa6-123">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="e1aa6-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e1aa6-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e1aa6-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e1aa6-125">Debugging</span></span>](index.md)
