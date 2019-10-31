---
title: ICorDebugDataTarget2 Arabirimi
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
ms.openlocfilehash: 3c59752949ca29cbd0ed5a34ec7aeb3d98b6f9b6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136492"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="f7660-102">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7660-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="f7660-103">[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="f7660-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f7660-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f7660-104">Methods</span></span>  
  
|<span data-ttu-id="f7660-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f7660-105">Method</span></span>|<span data-ttu-id="f7660-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7660-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f7660-107">CreateVirtualUnwinder Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7660-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="f7660-108">Bir başlangıç bağlamından (bir iş parçacığının yaprağı olması gerekmez) geriye doğru geri sarıdan başlayan yeni bir Stack unwinder oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7660-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="f7660-109">EnumerateThreadIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7660-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="f7660-110">Etkin iş parçacığı kimliklerinin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7660-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="f7660-111">GetImageFromPointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7660-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="f7660-112">Bu modüldeki bir adresten modül taban adresini ve boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7660-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="f7660-113">GetImageLocation Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7660-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="f7660-114">Modülün temel adresinden bir modülün yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7660-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="f7660-115">GetSymbolProviderForImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7660-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="f7660-116">Bu modülün temel adresinden bir modülün sembol sağlayıcısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7660-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7660-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7660-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7660-118">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7660-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f7660-119">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="f7660-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7660-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7660-120">Requirements</span></span>  
 <span data-ttu-id="f7660-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7660-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7660-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f7660-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7660-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f7660-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7660-124">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7660-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7660-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7660-125">See also</span></span>

- [<span data-ttu-id="f7660-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f7660-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f7660-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f7660-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
