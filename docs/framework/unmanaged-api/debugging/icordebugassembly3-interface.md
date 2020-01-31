---
title: ICorDebugAssembly3 Arabirimi
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: deb300ced2ff7a116bd443c9a7b10dcc0b7955ac
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784526"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="db7e5-102">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db7e5-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="db7e5-103">Kapsayıcı derlemeler ve içerdikleri derlemeler için destek sağlamak üzere ICorDebugAssembly arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="db7e5-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="db7e5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="db7e5-104">Methods</span></span>  
  
|<span data-ttu-id="db7e5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="db7e5-105">Method</span></span>|<span data-ttu-id="db7e5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db7e5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="db7e5-107">EnumerateContainedAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="db7e5-107">EnumerateContainedAssemblies Method</span></span>](icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="db7e5-108">Bu derlemede yer alan derlemeler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="db7e5-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="db7e5-109">GetContainerAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="db7e5-109">GetContainerAssembly Method</span></span>](icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="db7e5-110">Bu `ICorDebugAssembly3` nesnesinin kapsayıcı derlemesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="db7e5-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db7e5-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db7e5-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db7e5-112">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db7e5-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="db7e5-113">Bir arabirim işaretçisini almak için `QueryInterface` çağırma girişimi, .NET Native dışındaki ICorDebug senaryoları için `E_NOINTERFACE` döndürür.</span><span class="sxs-lookup"><span data-stu-id="db7e5-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db7e5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db7e5-114">Requirements</span></span>  
 <span data-ttu-id="db7e5-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db7e5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db7e5-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="db7e5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db7e5-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="db7e5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db7e5-118">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db7e5-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db7e5-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db7e5-119">See also</span></span>

- [<span data-ttu-id="db7e5-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="db7e5-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="db7e5-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="db7e5-121">Debugging</span></span>](index.md)
