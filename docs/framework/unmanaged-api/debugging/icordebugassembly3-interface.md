---
title: ICorDebugAssembly3 Arabirimi
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca77360c36ff2cdce7ee47d5c3883dd824c6cef8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959322"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="a8f4f-102">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8f4f-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="a8f4f-103">Kapsayıcı derlemeler ve içerdikleri derlemeler için destek sağlamak üzere ICorDebugAssembly arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="a8f4f-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8f4f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a8f4f-104">Methods</span></span>  
  
|<span data-ttu-id="a8f4f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a8f4f-105">Method</span></span>|<span data-ttu-id="a8f4f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8f4f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8f4f-107">EnumerateContainedAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8f4f-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="a8f4f-108">Bu derlemede yer alan derlemeler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="a8f4f-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="a8f4f-109">GetContainerAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8f4f-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="a8f4f-110">Bu `ICorDebugAssembly3` nesnenin kapsayıcı derlemesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a8f4f-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8f4f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8f4f-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8f4f-112">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8f4f-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="a8f4f-113">.NET Native dışında ICorDebug senaryolarına `QueryInterface` `E_NOINTERFACE` yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="a8f4f-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8f4f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8f4f-114">Requirements</span></span>  
 <span data-ttu-id="a8f4f-115">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8f4f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8f4f-116">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a8f4f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8f4f-117">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a8f4f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8f4f-118">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8f4f-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8f4f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8f4f-119">See also</span></span>

- [<span data-ttu-id="a8f4f-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a8f4f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a8f4f-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a8f4f-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
