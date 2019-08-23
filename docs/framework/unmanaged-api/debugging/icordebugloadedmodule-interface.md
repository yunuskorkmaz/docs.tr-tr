---
title: ICorDebugLoadedModule Arabirimi
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9da6aba61382381fc25fe70615976cd0e744ee1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910014"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="6c8af-102">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c8af-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="6c8af-103">Yüklü bir modül hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c8af-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c8af-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6c8af-104">Methods</span></span>  
  
|<span data-ttu-id="6c8af-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6c8af-105">Method</span></span>|<span data-ttu-id="6c8af-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c8af-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c8af-107">GetBaseAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c8af-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="6c8af-108">Yüklenen modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="6c8af-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="6c8af-109">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c8af-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="6c8af-110">Yüklenen modülün adını alır.</span><span class="sxs-lookup"><span data-stu-id="6c8af-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="6c8af-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c8af-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="6c8af-112">Yüklenen modülün bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="6c8af-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c8af-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c8af-113">Remarks</span></span>  
 <span data-ttu-id="6c8af-114">`ICorDebugLoadedModule` Arabirim bir hata ayıklayıcı tarafından uygulanır ve hata ayıklayıcıdan yüklenen modül hakkında bilgi almak için clr hata ayıklama arabirimleri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c8af-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6c8af-115">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c8af-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="6c8af-116">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="6c8af-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c8af-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c8af-117">Requirements</span></span>  
 <span data-ttu-id="6c8af-118">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c8af-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c8af-119">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6c8af-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c8af-120">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6c8af-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c8af-121">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c8af-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c8af-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c8af-122">See also</span></span>

- [<span data-ttu-id="6c8af-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6c8af-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6c8af-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6c8af-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
