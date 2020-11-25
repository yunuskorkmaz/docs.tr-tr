---
title: ICorDebugDataTarget2 Arabirimi
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
ms.openlocfilehash: aa1db39b564b987fb8d0f79d529f5af59b7e4c02
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713762"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="a4820-102">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4820-102">ICorDebugDataTarget2 Interface</span></span>

<span data-ttu-id="a4820-103">[ICorDebugDataTarget](icordebugdatatarget-interface.md)arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="a4820-103">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a4820-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a4820-104">Methods</span></span>  
  
|<span data-ttu-id="a4820-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a4820-105">Method</span></span>|<span data-ttu-id="a4820-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4820-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a4820-107">CreateVirtualUnwinder Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4820-107">CreateVirtualUnwinder Method</span></span>](icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="a4820-108">Bir başlangıç bağlamından (bir iş parçacığının yaprağı olması gerekmez) geriye doğru geri sarıdan başlayan yeni bir Stack unwinder oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a4820-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="a4820-109">EnumerateThreadIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4820-109">EnumerateThreadIDs Method</span></span>](icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="a4820-110">Etkin iş parçacığı kimliklerinin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4820-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="a4820-111">GetImageFromPointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4820-111">GetImageFromPointer Method</span></span>](icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="a4820-112">Bu modüldeki bir adresten modül taban adresini ve boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4820-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="a4820-113">GetImageLocation Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4820-113">GetImageLocation Method</span></span>](icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="a4820-114">Modülün temel adresinden bir modülün yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4820-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="a4820-115">GetSymbolProviderForImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4820-115">GetSymbolProviderForImage Method</span></span>](icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="a4820-116">Bu modülün temel adresinden bir modülün sembol sağlayıcısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4820-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4820-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4820-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4820-118">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4820-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="a4820-119">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="a4820-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4820-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4820-120">Requirements</span></span>  

 <span data-ttu-id="a4820-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4820-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4820-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a4820-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4820-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a4820-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4820-124">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4820-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4820-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4820-125">See also</span></span>

- [<span data-ttu-id="a4820-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a4820-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a4820-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a4820-127">Debugging</span></span>](index.md)
