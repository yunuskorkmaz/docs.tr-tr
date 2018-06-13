---
title: ICorDebugInstanceFieldSymbol arabirimi
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82f6ccd43059f33a69b8b052f9efa34c4e4f2c1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417722"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="cd6aa-102">ICorDebugInstanceFieldSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd6aa-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="cd6aa-103">Bir örnek alanındaki hata ayıklama sembol bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd6aa-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cd6aa-104">Methods</span></span>  
  
|<span data-ttu-id="cd6aa-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cd6aa-105">Method</span></span>|<span data-ttu-id="cd6aa-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd6aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd6aa-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd6aa-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="cd6aa-108">Örnek alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="cd6aa-109">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd6aa-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="cd6aa-110">Bu örnek alanı kendi üst sınıfı'bayt uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="cd6aa-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd6aa-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="cd6aa-112">Örnek alanı bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd6aa-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd6aa-113">Remarks</span></span>  
 <span data-ttu-id="cd6aa-114">`ICorDebugInstanceFieldSymbol` Arabirimi bir örnek alanındaki hata ayıklama sembol bilgilerini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd6aa-115">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="cd6aa-116">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd6aa-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd6aa-117">Requirements</span></span>  
 <span data-ttu-id="cd6aa-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd6aa-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd6aa-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd6aa-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd6aa-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd6aa-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd6aa-121">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd6aa-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd6aa-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-122">See Also</span></span>  
 [<span data-ttu-id="cd6aa-123">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd6aa-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="cd6aa-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cd6aa-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="cd6aa-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="cd6aa-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
