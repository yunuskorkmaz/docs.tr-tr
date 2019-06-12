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
ms.openlocfilehash: 256fd900fa73948b4ca42ac6b6f21f145effc461
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025887"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="b37c7-102">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b37c7-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="b37c7-103">Windows çalışma zamanı türleri bir uygulama etki alanında şu anda yüklü yönetilen gösterimleri hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b37c7-103">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="b37c7-104">Bu arabirim, Icordebugappdomain ve Icordebugappdomain2 arabirimlerinin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="b37c7-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b37c7-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b37c7-105">Methods</span></span>  
  
|<span data-ttu-id="b37c7-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b37c7-106">Method</span></span>|<span data-ttu-id="b37c7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b37c7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b37c7-108">Icordebugappdomain3::getcachedwinrttypes</span><span class="sxs-lookup"><span data-stu-id="b37c7-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="b37c7-109">Önbelleğe alınan tüm Windows çalışma zamanı türleri için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="b37c7-109">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="b37c7-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="b37c7-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="b37c7-111">Bir numaralandırıcı, kendi arabirimi tanımlayıcılarına göre bir uygulama etki alanındaki önbelleğe alınmış Windows çalışma zamanı türleri için alır.</span><span class="sxs-lookup"><span data-stu-id="b37c7-111">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b37c7-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b37c7-112">Remarks</span></span>  
 <span data-ttu-id="b37c7-113">Bu arabirim tarafından bir hata ayıklayıcı bir işlev değerlendirmesi çağrısı ile birlikte kullanılmak üzere tasarlanmıştır `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span><span class="sxs-lookup"><span data-stu-id="b37c7-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="b37c7-114">Yöntemi bir Windows çalışma zamanı sunucu nesnesi tarafından desteklenen arabirim tanımlayıcıları aldığında, hata ayıklayıcı Bu arabirimler için karşılık gelen yönetilen türler eşlemek için bu arabirimde tanımlanan yöntemler kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="b37c7-114">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="b37c7-115">Bu arabirim örneğini almak için çalıştırın `QueryInterface` Icordebugappdomain veya Icordebugappdomain2 arabirimi örneği üzerinde.</span><span class="sxs-lookup"><span data-stu-id="b37c7-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b37c7-116">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b37c7-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b37c7-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b37c7-117">Requirements</span></span>  
 <span data-ttu-id="b37c7-118">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="b37c7-118">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="b37c7-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b37c7-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b37c7-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b37c7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b37c7-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b37c7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b37c7-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b37c7-122">See also</span></span>

- [<span data-ttu-id="b37c7-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b37c7-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
