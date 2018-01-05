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
ms.workload: dotnet
ms.openlocfilehash: e581b4256da2ecc19a8b97520e0e70fef972b549
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="75773-102">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75773-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="75773-103">Mantıksal olarak kapsayıcı derlemeler ve bunların içerdiği derlemeler için destek sağlamak için Icordebugassembly arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="75773-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75773-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="75773-104">Methods</span></span>  
  
|<span data-ttu-id="75773-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="75773-105">Method</span></span>|<span data-ttu-id="75773-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75773-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75773-107">EnumerateContainedAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75773-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="75773-108">Bu derlemede bulunan derlemeler için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="75773-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="75773-109">GetContainerAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75773-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="75773-110">Bu kapsayıcı derleme döndürür `ICorDebugAssembly3` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="75773-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75773-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75773-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75773-112">Arabirimi yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="75773-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="75773-113">Çağrı girişimi `QueryInterface` bir arabirim işaretçisi almak için döndürür `E_NOINTERFACE` .NET yerel dışında Icordebug senaryoları için.</span><span class="sxs-lookup"><span data-stu-id="75773-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75773-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75773-114">Requirements</span></span>  
 <span data-ttu-id="75773-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75773-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75773-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75773-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75773-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75773-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75773-118">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75773-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75773-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="75773-119">See Also</span></span>  
 [<span data-ttu-id="75773-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="75773-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="75773-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="75773-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
