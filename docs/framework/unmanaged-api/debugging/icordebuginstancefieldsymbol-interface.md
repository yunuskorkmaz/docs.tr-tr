---
title: Icordebugınstancefieldsymbol arabirimi
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 082d8e8c8b57b7d0938f59aebbe08e35a7e3f7df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560754"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="67e08-102">Icordebugınstancefieldsymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="67e08-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="67e08-103">Bir örnek alanıyla hata ayıklama sembolü bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="67e08-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="67e08-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="67e08-104">Methods</span></span>  
  
|<span data-ttu-id="67e08-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="67e08-105">Method</span></span>|<span data-ttu-id="67e08-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67e08-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="67e08-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67e08-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="67e08-108">Örnek alanı adını alır.</span><span class="sxs-lookup"><span data-stu-id="67e08-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="67e08-109">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67e08-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="67e08-110">Bu örnek alanı kendi üst sınıfı'bayt uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="67e08-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="67e08-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67e08-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="67e08-112">Örnek alanı bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="67e08-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67e08-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67e08-113">Remarks</span></span>  
 <span data-ttu-id="67e08-114">`ICorDebugInstanceFieldSymbol` Arabirimi, bir örnek alanıyla hata ayıklama sembolü bilgilerini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67e08-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67e08-115">Bu arabirim yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="67e08-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="67e08-116">Bu arabirim .NET Native dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="67e08-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67e08-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67e08-117">Requirements</span></span>  
 <span data-ttu-id="67e08-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67e08-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67e08-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67e08-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67e08-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67e08-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67e08-121">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67e08-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67e08-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67e08-122">See also</span></span>
- [<span data-ttu-id="67e08-123">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67e08-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="67e08-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="67e08-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="67e08-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="67e08-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
