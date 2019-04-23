---
title: ICorDebugLoadedModule Arabirimi
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e91dda9cbc5957768e98db2b2a9e1026d94c03e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200759"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="75a15-102">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75a15-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="75a15-103">Yüklenen bir modülün hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="75a15-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75a15-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="75a15-104">Methods</span></span>  
  
|<span data-ttu-id="75a15-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="75a15-105">Method</span></span>|<span data-ttu-id="75a15-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75a15-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75a15-107">GetBaseAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75a15-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="75a15-108">Yüklenen bir modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="75a15-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="75a15-109">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75a15-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="75a15-110">Yüklenen bir modülün adını alır.</span><span class="sxs-lookup"><span data-stu-id="75a15-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="75a15-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75a15-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="75a15-112">Yüklenen bir modülün bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="75a15-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75a15-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75a15-113">Remarks</span></span>  
 <span data-ttu-id="75a15-114">`ICorDebugLoadedModule` Arabirimi bir hata ayıklayıcı tarafından uygulanır ve hata ayıklayıcı'dan yüklenen bir modülün hakkında bilgi almak için CLR hata ayıklama arabirimleri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="75a15-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75a15-115">Bu arabirim yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="75a15-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="75a15-116">Bu arabirim .NET Native dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="75a15-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75a15-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75a15-117">Requirements</span></span>  
 <span data-ttu-id="75a15-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75a15-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75a15-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75a15-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75a15-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75a15-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75a15-121">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75a15-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75a15-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75a15-122">See also</span></span>

- [<span data-ttu-id="75a15-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="75a15-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="75a15-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="75a15-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
