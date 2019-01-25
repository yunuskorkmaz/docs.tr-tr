---
title: ICorDebugDataTarget2 Arabirimi
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0931cb5ed133d4de82473ae786f28f13fd396db5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743016"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="497fe-102">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="497fe-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="497fe-103">Mantıksal olarak genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)arabirimi.</span><span class="sxs-lookup"><span data-stu-id="497fe-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="497fe-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="497fe-104">Methods</span></span>  
  
|<span data-ttu-id="497fe-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="497fe-105">Method</span></span>|<span data-ttu-id="497fe-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="497fe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="497fe-107">CreateVirtualUnwinder Yöntemi</span><span class="sxs-lookup"><span data-stu-id="497fe-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="497fe-108">(Bu mutlaka bir iş parçacığının yaprak olmayan) bir ilk bağlamından geriye doğru izleme başlayan yeni bir yığın unwinder oluşturur.</span><span class="sxs-lookup"><span data-stu-id="497fe-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="497fe-109">EnumerateThreadIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="497fe-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="497fe-110">Etkin iş parçacığı kimliklerinin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="497fe-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="497fe-111">GetImageFromPointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="497fe-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="497fe-112">Bu modüldeki bir adresinden modülü temel adres ve boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="497fe-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="497fe-113">GetImageLocation Yöntemi</span><span class="sxs-lookup"><span data-stu-id="497fe-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="497fe-114">Modülün temel adres bir modülün yolu döndürür.</span><span class="sxs-lookup"><span data-stu-id="497fe-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="497fe-115">GetSymbolProviderForImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="497fe-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="497fe-116">Bir modül için Sembol sağlayıcısı Bu modülün temel adres döndürür.</span><span class="sxs-lookup"><span data-stu-id="497fe-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="497fe-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="497fe-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="497fe-118">Bu arabirim yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="497fe-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="497fe-119">Bu arabirim .NET Native dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="497fe-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="497fe-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="497fe-120">Requirements</span></span>  
 <span data-ttu-id="497fe-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="497fe-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="497fe-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="497fe-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="497fe-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="497fe-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="497fe-124">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="497fe-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="497fe-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="497fe-125">See also</span></span>
- [<span data-ttu-id="497fe-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="497fe-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="497fe-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="497fe-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
