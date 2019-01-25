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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ade4c88f4431dd6db636ea2581bdb936ac8d8e5f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538017"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="7f078-102">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f078-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="7f078-103">Yönetilen gösterimleri hakkında bilgi almak için yöntemler sağlar [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türleri bir uygulama etki alanında şu anda yüklü.</span><span class="sxs-lookup"><span data-stu-id="7f078-103">Provides methods to retrieve information about the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in an application domain.</span></span> <span data-ttu-id="7f078-104">Bu arabirim, Icordebugappdomain ve Icordebugappdomain2 arabirimlerinin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="7f078-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7f078-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7f078-105">Methods</span></span>  
  
|<span data-ttu-id="7f078-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7f078-106">Method</span></span>|<span data-ttu-id="7f078-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f078-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7f078-108">Icordebugappdomain3::getcachedwinrttypes</span><span class="sxs-lookup"><span data-stu-id="7f078-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="7f078-109">Önbelleğe alınmış tüm için bir numaralandırıcı alır [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türleri.</span><span class="sxs-lookup"><span data-stu-id="7f078-109">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>|  
|[<span data-ttu-id="7f078-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="7f078-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="7f078-111">Önbelleğe alınmış için bir numaralandırıcı alır [!INCLUDE[wrt](../../../../includes/wrt-md.md)] temel alarak kendi arabirimi tanımlayıcılarını uygulama etki alanında tür.</span><span class="sxs-lookup"><span data-stu-id="7f078-111">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f078-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f078-112">Remarks</span></span>  
 <span data-ttu-id="7f078-113">Bu arabirim tarafından bir hata ayıklayıcı bir işlev değerlendirmesi çağrısı ile birlikte kullanılmak üzere tasarlanmıştır `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span><span class="sxs-lookup"><span data-stu-id="7f078-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="7f078-114">Yöntemi tarafından desteklenen arabirim tanımlayıcıları zaman alır bir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] sunucu nesne, hata ayıklayıcı Bu arabirimler için karşılık gelen yönetilen türler eşlemek için bu arabirimde tanımlanan yöntemler kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="7f078-114">When the method retrieves the interface identifiers supported by a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="7f078-115">Bu arabirim örneğini almak için çalıştırın `QueryInterface` Icordebugappdomain veya Icordebugappdomain2 arabirimi örneği üzerinde.</span><span class="sxs-lookup"><span data-stu-id="7f078-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f078-116">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7f078-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f078-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f078-117">Requirements</span></span>  
 <span data-ttu-id="7f078-118">**Platformlar:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f078-118">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="7f078-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f078-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f078-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f078-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f078-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f078-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f078-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f078-122">See also</span></span>
- [<span data-ttu-id="7f078-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7f078-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
