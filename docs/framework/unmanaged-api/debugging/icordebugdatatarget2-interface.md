---
title: ICorDebugDataTarget2 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 034e7d46c1b38aecdab18ea3a7d3b149b3d59369
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="e598b-102">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e598b-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="e598b-103">Mantıksal olarak genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e598b-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e598b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e598b-104">Methods</span></span>  
  
|<span data-ttu-id="e598b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e598b-105">Method</span></span>|<span data-ttu-id="e598b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e598b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e598b-107">CreateVirtualUnwinder yöntemi</span><span class="sxs-lookup"><span data-stu-id="e598b-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="e598b-108">Geriye doğru izleme (hangi mutlaka bir iş parçacığı yaprak olmayan) bir ilk bağlamından başlayan yeni bir yığın unwinder oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e598b-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="e598b-109">Enumeratethreadıds yöntemi</span><span class="sxs-lookup"><span data-stu-id="e598b-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="e598b-110">Etkin iş parçacığı kimlikleri listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e598b-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="e598b-111">Getımagefrompointer yöntemi</span><span class="sxs-lookup"><span data-stu-id="e598b-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="e598b-112">Bu modüldeki bir adresinden modülü taban adresi ve boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e598b-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="e598b-113">Getımagelocation yöntemi</span><span class="sxs-lookup"><span data-stu-id="e598b-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="e598b-114">Yolun bir modül modülün temel adresinden döndürür.</span><span class="sxs-lookup"><span data-stu-id="e598b-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="e598b-115">Getsymbolproviderforımage yöntemi</span><span class="sxs-lookup"><span data-stu-id="e598b-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="e598b-116">Bir modül için simge sağlayıcısı bu modül temel adresinden döndürür.</span><span class="sxs-lookup"><span data-stu-id="e598b-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e598b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e598b-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e598b-118">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e598b-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e598b-119">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="e598b-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e598b-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e598b-120">Requirements</span></span>  
 <span data-ttu-id="e598b-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e598b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e598b-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e598b-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e598b-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e598b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e598b-124">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e598b-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e598b-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e598b-125">See Also</span></span>  
 [<span data-ttu-id="e598b-126">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e598b-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e598b-127">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e598b-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
