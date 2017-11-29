---
title: ICorDebugAssembly3 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9ed476746e627be987e6307bd367f0d16374de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="71763-102">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71763-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="71763-103">Mantıksal olarak kapsayıcı derlemeler ve bunların içerdiği derlemeler için destek sağlamak için Icordebugassembly arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="71763-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="71763-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="71763-104">Methods</span></span>  
  
|<span data-ttu-id="71763-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="71763-105">Method</span></span>|<span data-ttu-id="71763-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71763-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="71763-107">EnumerateContainedAssemblies yöntemi</span><span class="sxs-lookup"><span data-stu-id="71763-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="71763-108">Bu derlemede bulunan derlemeler için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="71763-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="71763-109">GetContainerAssembly yöntemi</span><span class="sxs-lookup"><span data-stu-id="71763-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="71763-110">Bu kapsayıcı derleme döndürür `ICorDebugAssembly3` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="71763-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71763-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71763-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71763-112">Arabirimi yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71763-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="71763-113">Çağrı girişimi `QueryInterface` bir arabirim işaretçisi almak için döndürür `E_NOINTERFACE` .NET yerel dışında Icordebug senaryoları için.</span><span class="sxs-lookup"><span data-stu-id="71763-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71763-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71763-114">Requirements</span></span>  
 <span data-ttu-id="71763-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71763-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71763-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71763-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71763-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71763-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71763-118">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71763-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71763-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71763-119">See Also</span></span>  
 [<span data-ttu-id="71763-120">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="71763-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="71763-121">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="71763-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
