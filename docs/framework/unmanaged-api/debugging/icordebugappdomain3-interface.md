---
description: 'Daha fazla bilgi edinin: ICorDebugAppDomain3 Interface'
title: ICorDebugAppDomain3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
ms.openlocfilehash: 6575aa685759102443babeaf82774e6221b80693
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772217"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="bec81-103">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bec81-103">ICorDebugAppDomain3 Interface</span></span>

<span data-ttu-id="bec81-104">Bir uygulama etki alanında yüklü olan Windows Çalışma Zamanı türlerinin yönetilen temsilleri hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bec81-104">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="bec81-105">Bu arabirim, ICorDebugAppDomain ve ICorDebugAppDomain2 arabirimlerinin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="bec81-105">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bec81-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bec81-106">Methods</span></span>  
  
|<span data-ttu-id="bec81-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bec81-107">Method</span></span>|<span data-ttu-id="bec81-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bec81-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bec81-109">ICorDebugAppDomain3:: Getcachedwınrttypes</span><span class="sxs-lookup"><span data-stu-id="bec81-109">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="bec81-110">Tüm önbelleğe alınmış Windows Çalışma Zamanı türleri için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="bec81-110">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="bec81-111">ICorDebugAppDomain3:: Getcachedwinrttypesforiıds</span><span class="sxs-lookup"><span data-stu-id="bec81-111">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="bec81-112">Bir uygulama etki alanındaki önbelleğe alınmış Windows Çalışma Zamanı türleri için kendi arabirim tanımlayıcılarına göre bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="bec81-112">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bec81-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bec81-113">Remarks</span></span>  

 <span data-ttu-id="bec81-114">Bu arabirim bir hata ayıklayıcı tarafından, bir işlev değerlendirme çağrısıyla birlikte kullanılmak üzere tasarlanmıştır `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)` .</span><span class="sxs-lookup"><span data-stu-id="bec81-114">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="bec81-115">Yöntemi bir Windows Çalışma Zamanı sunucusu nesnesi tarafından desteklenen arabirim tanımlayıcılarını aldığında, hata ayıklayıcı bu arayüzlere karşılık gelen yönetilen türlerle eşlemek için bu arabirimde tanımlanan yöntemleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="bec81-115">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="bec81-116">Bu arabirimin bir örneğini almak için `QueryInterface` ICorDebugAppDomain veya ICorDebugAppDomain2 arabiriminin bir örneği üzerinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bec81-116">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bec81-117">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="bec81-117">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bec81-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bec81-118">Requirements</span></span>  

 <span data-ttu-id="bec81-119">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="bec81-119">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="bec81-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bec81-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bec81-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bec81-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bec81-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bec81-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec81-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bec81-123">See also</span></span>

- [<span data-ttu-id="bec81-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bec81-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
