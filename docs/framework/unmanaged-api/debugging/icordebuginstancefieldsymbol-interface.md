---
title: ICorDebugInstanceFieldSymbol arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fbf3f07f5669c4fcafa4d3cc4119fc715539651d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="64922-102">ICorDebugInstanceFieldSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="64922-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="64922-103">Bir örnek alanındaki hata ayıklama sembol bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="64922-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="64922-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="64922-104">Methods</span></span>  
  
|<span data-ttu-id="64922-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="64922-105">Method</span></span>|<span data-ttu-id="64922-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64922-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64922-107">GetName yöntemi</span><span class="sxs-lookup"><span data-stu-id="64922-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="64922-108">Örnek alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="64922-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="64922-109">GetOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="64922-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="64922-110">Bu örnek alanı kendi üst sınıfı'bayt uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="64922-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="64922-111">GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="64922-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="64922-112">Örnek alanı bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="64922-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64922-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64922-113">Remarks</span></span>  
 <span data-ttu-id="64922-114">`ICorDebugInstanceFieldSymbol` Arabirimi bir örnek alanındaki hata ayıklama sembol bilgilerini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="64922-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64922-115">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="64922-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="64922-116">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="64922-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64922-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64922-117">Requirements</span></span>  
 <span data-ttu-id="64922-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64922-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64922-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64922-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64922-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64922-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64922-121">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64922-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64922-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="64922-122">See Also</span></span>  
 [<span data-ttu-id="64922-123">ICorDebugStaticFieldSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="64922-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="64922-124">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="64922-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="64922-125">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="64922-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
