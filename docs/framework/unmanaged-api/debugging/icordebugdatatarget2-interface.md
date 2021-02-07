---
description: 'Daha fazla bilgi edinin: ICorDebugDataTarget2 Interface'
title: ICorDebugDataTarget2 Arabirimi
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
ms.openlocfilehash: 13a83ee99f0158f32f466f9ae29af3d917248f95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710471"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="46a31-103">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46a31-103">ICorDebugDataTarget2 Interface</span></span>

<span data-ttu-id="46a31-104">[ICorDebugDataTarget](icordebugdatatarget-interface.md)arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="46a31-104">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46a31-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="46a31-105">Methods</span></span>  
  
|<span data-ttu-id="46a31-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="46a31-106">Method</span></span>|<span data-ttu-id="46a31-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46a31-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="46a31-108">CreateVirtualUnwinder Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46a31-108">CreateVirtualUnwinder Method</span></span>](icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="46a31-109">Bir başlangıç bağlamından (bir iş parçacığının yaprağı olması gerekmez) geriye doğru geri sarıdan başlayan yeni bir Stack unwinder oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46a31-109">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="46a31-110">EnumerateThreadIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46a31-110">EnumerateThreadIDs Method</span></span>](icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="46a31-111">Etkin iş parçacığı kimliklerinin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="46a31-111">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="46a31-112">GetImageFromPointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46a31-112">GetImageFromPointer Method</span></span>](icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="46a31-113">Bu modüldeki bir adresten modül taban adresini ve boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="46a31-113">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="46a31-114">GetImageLocation Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46a31-114">GetImageLocation Method</span></span>](icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="46a31-115">Modülün temel adresinden bir modülün yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="46a31-115">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="46a31-116">GetSymbolProviderForImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46a31-116">GetSymbolProviderForImage Method</span></span>](icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="46a31-117">Bu modülün temel adresinden bir modülün sembol sağlayıcısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="46a31-117">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46a31-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46a31-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46a31-119">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="46a31-119">This interface is available with .NET Native only.</span></span> <span data-ttu-id="46a31-120">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="46a31-120">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46a31-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46a31-121">Requirements</span></span>  

 <span data-ttu-id="46a31-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46a31-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46a31-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="46a31-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46a31-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="46a31-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46a31-125">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46a31-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46a31-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46a31-126">See also</span></span>

- [<span data-ttu-id="46a31-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="46a31-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="46a31-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="46a31-128">Debugging</span></span>](index.md)
