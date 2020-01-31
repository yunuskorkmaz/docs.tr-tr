---
title: ICorDebugLoadedModule Arabirimi
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: 9d3bdcec9e90dab337b595294d114de4bd3d531f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781994"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="f0b09-102">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0b09-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="f0b09-103">Yüklü bir modül hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0b09-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0b09-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f0b09-104">Methods</span></span>  
  
|<span data-ttu-id="f0b09-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f0b09-105">Method</span></span>|<span data-ttu-id="f0b09-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0b09-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0b09-107">GetBaseAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0b09-107">GetBaseAddress Method</span></span>](icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="f0b09-108">Yüklenen modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="f0b09-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="f0b09-109">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0b09-109">GetName Method</span></span>](icordebugloadedmodule-getname-method.md)|<span data-ttu-id="f0b09-110">Yüklenen modülün adını alır.</span><span class="sxs-lookup"><span data-stu-id="f0b09-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="f0b09-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0b09-111">GetSize Method</span></span>](icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="f0b09-112">Yüklenen modülün bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="f0b09-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0b09-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0b09-113">Remarks</span></span>  
 <span data-ttu-id="f0b09-114">`ICorDebugLoadedModule` arabirimi bir hata ayıklayıcı tarafından uygulanır ve hata ayıklayıcıdan yüklenen modül hakkında bilgi almak için CLR hata ayıklama arabirimleri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0b09-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0b09-115">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0b09-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f0b09-116">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="f0b09-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0b09-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0b09-117">Requirements</span></span>  
 <span data-ttu-id="f0b09-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0b09-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0b09-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f0b09-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0b09-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f0b09-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0b09-121">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0b09-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0b09-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0b09-122">See also</span></span>

- [<span data-ttu-id="f0b09-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f0b09-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f0b09-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f0b09-124">Debugging</span></span>](index.md)
