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
ms.workload: dotnet
ms.openlocfilehash: 2aefdb34277d2cb7ebc29ef817745b85064475d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="37d00-102">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37d00-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="37d00-103">Mantıksal olarak genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)arabirimi.</span><span class="sxs-lookup"><span data-stu-id="37d00-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="37d00-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="37d00-104">Methods</span></span>  
  
|<span data-ttu-id="37d00-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="37d00-105">Method</span></span>|<span data-ttu-id="37d00-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37d00-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="37d00-107">CreateVirtualUnwinder Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37d00-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="37d00-108">Geriye doğru izleme (hangi mutlaka bir iş parçacığı yaprak olmayan) bir ilk bağlamından başlayan yeni bir yığın unwinder oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37d00-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="37d00-109">EnumerateThreadIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37d00-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="37d00-110">Etkin iş parçacığı kimlikleri listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="37d00-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="37d00-111">GetImageFromPointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37d00-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="37d00-112">Bu modüldeki bir adresinden modülü taban adresi ve boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="37d00-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="37d00-113">GetImageLocation Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37d00-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="37d00-114">Yolun bir modül modülün temel adresinden döndürür.</span><span class="sxs-lookup"><span data-stu-id="37d00-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="37d00-115">GetSymbolProviderForImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37d00-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="37d00-116">Bir modül için simge sağlayıcısı bu modül temel adresinden döndürür.</span><span class="sxs-lookup"><span data-stu-id="37d00-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37d00-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37d00-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37d00-118">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="37d00-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="37d00-119">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="37d00-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37d00-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37d00-120">Requirements</span></span>  
 <span data-ttu-id="37d00-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37d00-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37d00-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37d00-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37d00-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37d00-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37d00-124">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37d00-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37d00-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37d00-125">See Also</span></span>  
 [<span data-ttu-id="37d00-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="37d00-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="37d00-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="37d00-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
