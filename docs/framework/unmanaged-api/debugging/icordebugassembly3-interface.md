---
description: 'Daha fazla bilgi edinin: ICorDebugAssembly3 Interface'
title: ICorDebugAssembly3 Arabirimi
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 3a8cabf41dffa75d82c2b6fde53dff2ede4838e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791510"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="0b3d8-103">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b3d8-103">ICorDebugAssembly3 Interface</span></span>

<span data-ttu-id="0b3d8-104">Kapsayıcı derlemeler ve içerdikleri derlemeler için destek sağlamak üzere ICorDebugAssembly arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="0b3d8-104">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0b3d8-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0b3d8-105">Methods</span></span>  
  
|<span data-ttu-id="0b3d8-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0b3d8-106">Method</span></span>|<span data-ttu-id="0b3d8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b3d8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b3d8-108">EnumerateContainedAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b3d8-108">EnumerateContainedAssemblies Method</span></span>](icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="0b3d8-109">Bu derlemede yer alan derlemeler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="0b3d8-109">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="0b3d8-110">GetContainerAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b3d8-110">GetContainerAssembly Method</span></span>](icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="0b3d8-111">Bu nesnenin kapsayıcı derlemesini döndürür `ICorDebugAssembly3` .</span><span class="sxs-lookup"><span data-stu-id="0b3d8-111">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b3d8-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b3d8-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b3d8-113">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0b3d8-113">The interface is available with .NET Native only.</span></span> <span data-ttu-id="0b3d8-114">`QueryInterface` `E_NOINTERFACE` .NET Native dışında ICorDebug senaryolarına yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="0b3d8-114">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b3d8-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b3d8-115">Requirements</span></span>  

 <span data-ttu-id="0b3d8-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b3d8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b3d8-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0b3d8-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b3d8-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0b3d8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b3d8-119">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b3d8-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b3d8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b3d8-120">See also</span></span>

- [<span data-ttu-id="0b3d8-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0b3d8-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0b3d8-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0b3d8-122">Debugging</span></span>](index.md)
