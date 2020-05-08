---
title: ICorDebugAssembly3 Arabirimi
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 67707092c80b0e07aa284336c426aba09ff991af
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894823"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="9c4a6-102">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c4a6-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="9c4a6-103">Kapsayıcı derlemeler ve içerdikleri derlemeler için destek sağlamak üzere ICorDebugAssembly arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="9c4a6-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9c4a6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9c4a6-104">Methods</span></span>  
  
|<span data-ttu-id="9c4a6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9c4a6-105">Method</span></span>|<span data-ttu-id="9c4a6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c4a6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9c4a6-107">EnumerateContainedAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c4a6-107">EnumerateContainedAssemblies Method</span></span>](icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="9c4a6-108">Bu derlemede yer alan derlemeler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="9c4a6-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="9c4a6-109">GetContainerAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c4a6-109">GetContainerAssembly Method</span></span>](icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="9c4a6-110">Bu `ICorDebugAssembly3` nesnenin kapsayıcı derlemesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9c4a6-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c4a6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c4a6-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c4a6-112">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9c4a6-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="9c4a6-113">.NET Native dışında ICorDebug senaryolarına `QueryInterface` `E_NOINTERFACE` yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="9c4a6-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c4a6-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c4a6-114">Requirements</span></span>  
 <span data-ttu-id="9c4a6-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c4a6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c4a6-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9c4a6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c4a6-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9c4a6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c4a6-118">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c4a6-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c4a6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c4a6-119">See also</span></span>

- [<span data-ttu-id="9c4a6-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9c4a6-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9c4a6-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9c4a6-121">Debugging</span></span>](index.md)
