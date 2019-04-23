---
title: ICorDebugAssembly3 Arabirimi
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eecb135e034c3565e805ea776115579488b2a4d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210314"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="d1c99-102">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1c99-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="d1c99-103">Icordebugassembly arabirimi kapsayıcı derlemeleri ve bunların içerdiği derlemeleri için destek sağlamak için mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="d1c99-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d1c99-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d1c99-104">Methods</span></span>  
  
|<span data-ttu-id="d1c99-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d1c99-105">Method</span></span>|<span data-ttu-id="d1c99-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1c99-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d1c99-107">EnumerateContainedAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1c99-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="d1c99-108">Bu derlemede bulunan derlemeler için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="d1c99-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="d1c99-109">GetContainerAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1c99-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="d1c99-110">Bu kapsayıcı derleme döndürür `ICorDebugAssembly3` nesne.</span><span class="sxs-lookup"><span data-stu-id="d1c99-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1c99-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1c99-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1c99-112">Arabirimi yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1c99-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="d1c99-113">Arama girişimi `QueryInterface` bir arabirim işaretçisini almak için döndürür `E_NOINTERFACE` .NET Native dışında Icordebug senaryolar için.</span><span class="sxs-lookup"><span data-stu-id="d1c99-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1c99-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1c99-114">Requirements</span></span>  
 <span data-ttu-id="d1c99-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1c99-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1c99-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1c99-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1c99-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1c99-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1c99-118">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1c99-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c99-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1c99-119">See also</span></span>

- [<span data-ttu-id="d1c99-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d1c99-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d1c99-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d1c99-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
