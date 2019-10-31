---
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
ms.openlocfilehash: 0b238a953fa5cd57c8b7af9a0643bfc36ee1032e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088855"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="9043f-102">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9043f-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="9043f-103">Bir uygulama etki alanında yüklü olan Windows Çalışma Zamanı türlerinin yönetilen temsilleri hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9043f-103">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="9043f-104">Bu arabirim, ICorDebugAppDomain ve ICorDebugAppDomain2 arabirimlerinin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="9043f-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9043f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9043f-105">Methods</span></span>  
  
|<span data-ttu-id="9043f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9043f-106">Method</span></span>|<span data-ttu-id="9043f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9043f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9043f-108">ICorDebugAppDomain3:: Getcachedwınrttypes</span><span class="sxs-lookup"><span data-stu-id="9043f-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="9043f-109">Tüm önbelleğe alınmış Windows Çalışma Zamanı türleri için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="9043f-109">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="9043f-110">ICorDebugAppDomain3:: Getcachedwinrttypesforiıds</span><span class="sxs-lookup"><span data-stu-id="9043f-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="9043f-111">Bir uygulama etki alanındaki önbelleğe alınmış Windows Çalışma Zamanı türleri için kendi arabirim tanımlayıcılarına göre bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="9043f-111">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9043f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9043f-112">Remarks</span></span>  
 <span data-ttu-id="9043f-113">Bu arabirim, bir hata ayıklayıcı tarafından `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`bir işlev değerlendirme çağrısıyla birlikte kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9043f-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="9043f-114">Yöntemi bir Windows Çalışma Zamanı sunucusu nesnesi tarafından desteklenen arabirim tanımlayıcılarını aldığında, hata ayıklayıcı bu arayüzlere karşılık gelen yönetilen türlerle eşlemek için bu arabirimde tanımlanan yöntemleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="9043f-114">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="9043f-115">Bu arabirimin bir örneğini almak için ICorDebugAppDomain veya ICorDebugAppDomain2 arabiriminin bir örneği üzerinde `QueryInterface` çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9043f-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9043f-116">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="9043f-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9043f-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9043f-117">Requirements</span></span>  
 <span data-ttu-id="9043f-118">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="9043f-118">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="9043f-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9043f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9043f-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9043f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9043f-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9043f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9043f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9043f-122">See also</span></span>

- [<span data-ttu-id="9043f-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9043f-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
