---
title: ICorDebugLoadedModule Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4cc7a36deb7c81ccf67427b833dead7127619b39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="a4106-102">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4106-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="a4106-103">Yüklenen modülü hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4106-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a4106-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a4106-104">Methods</span></span>  
  
|<span data-ttu-id="a4106-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a4106-105">Method</span></span>|<span data-ttu-id="a4106-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4106-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a4106-107">GetBaseAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4106-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="a4106-108">Yüklenen modülün taban adresi alır.</span><span class="sxs-lookup"><span data-stu-id="a4106-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="a4106-109">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4106-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="a4106-110">Yüklenen modül adını alır.</span><span class="sxs-lookup"><span data-stu-id="a4106-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="a4106-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4106-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="a4106-112">Yüklenen modülün bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="a4106-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4106-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4106-113">Remarks</span></span>  
 <span data-ttu-id="a4106-114">`ICorDebugLoadedModule` Arabirimi bir hata ayıklayıcı tarafından uygulanır ve hata ayıklama arabirimleri CLR tarafından hata ayıklayıcı'dan yüklenen modülü hakkında bilgi almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4106-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4106-115">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4106-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="a4106-116">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="a4106-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4106-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4106-117">Requirements</span></span>  
 <span data-ttu-id="a4106-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4106-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4106-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4106-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4106-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4106-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4106-121">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4106-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4106-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a4106-122">See Also</span></span>  
 [<span data-ttu-id="a4106-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a4106-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a4106-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a4106-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
