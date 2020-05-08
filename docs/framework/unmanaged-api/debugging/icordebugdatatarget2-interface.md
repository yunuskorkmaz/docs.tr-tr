---
title: ICorDebugDataTarget2 Arabirimi
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
ms.openlocfilehash: 1c598d23cac77e50cf302e6936b88b5eb6e558c2
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976441"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="1aacb-102">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1aacb-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="1aacb-103">[ICorDebugDataTarget](icordebugdatatarget-interface.md)arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="1aacb-103">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1aacb-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1aacb-104">Methods</span></span>  
  
|<span data-ttu-id="1aacb-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1aacb-105">Method</span></span>|<span data-ttu-id="1aacb-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1aacb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1aacb-107">CreateVirtualUnwinder Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aacb-107">CreateVirtualUnwinder Method</span></span>](icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="1aacb-108">Bir başlangıç bağlamından (bir iş parçacığının yaprağı olması gerekmez) geriye doğru geri sarıdan başlayan yeni bir Stack unwinder oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1aacb-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="1aacb-109">EnumerateThreadIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aacb-109">EnumerateThreadIDs Method</span></span>](icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="1aacb-110">Etkin iş parçacığı kimliklerinin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1aacb-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="1aacb-111">GetImageFromPointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aacb-111">GetImageFromPointer Method</span></span>](icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="1aacb-112">Bu modüldeki bir adresten modül taban adresini ve boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1aacb-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="1aacb-113">GetImageLocation Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aacb-113">GetImageLocation Method</span></span>](icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="1aacb-114">Modülün temel adresinden bir modülün yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1aacb-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="1aacb-115">GetSymbolProviderForImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aacb-115">GetSymbolProviderForImage Method</span></span>](icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="1aacb-116">Bu modülün temel adresinden bir modülün sembol sağlayıcısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="1aacb-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1aacb-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1aacb-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1aacb-118">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1aacb-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="1aacb-119">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="1aacb-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aacb-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1aacb-120">Requirements</span></span>  
 <span data-ttu-id="1aacb-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1aacb-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aacb-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1aacb-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1aacb-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1aacb-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1aacb-124">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aacb-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aacb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1aacb-125">See also</span></span>

- [<span data-ttu-id="1aacb-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1aacb-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1aacb-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1aacb-127">Debugging</span></span>](index.md)
