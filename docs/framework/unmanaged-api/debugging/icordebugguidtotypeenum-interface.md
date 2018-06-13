---
title: ICorDebugGuidToTypeEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91d653587d5b7c35a2a43c7eed7c4bf33e5401f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416757"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="99001-102">ICorDebugGuidToTypeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99001-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="99001-103">Icordebugtype örnekleri tarafından temsil edilen bunların karşılık gelen türlerine ve GUID'ler kümesi arasında eşleme tanımlayan bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="99001-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="99001-104">Bu arabirim yöntemleri Icordebugenum arabiriminden devralır.</span><span class="sxs-lookup"><span data-stu-id="99001-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99001-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="99001-105">Methods</span></span>  
  
|<span data-ttu-id="99001-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="99001-106">Method</span></span>|<span data-ttu-id="99001-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99001-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99001-108">Icordebugguidtotypeenum::Next</span><span class="sxs-lookup"><span data-stu-id="99001-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="99001-109">Belirtilen sayıda alır [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) bilgilerini yazmak için GUID'leri eşleme örnekleri.</span><span class="sxs-lookup"><span data-stu-id="99001-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99001-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99001-110">Remarks</span></span>  
 <span data-ttu-id="99001-111">Bir `ICorDebugGuidToTypeEnum` arabirimi nesnesi çağırarak alınabilir [Icordebugappdomain3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99001-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="99001-112">Bir hata ayıklayıcısı bu arabirimin çağırabilirsiniz [sonraki](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) alma yöntemi [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) eşleşmelerini temsil eden nesneler yönetilen gösterimlerini [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türleri yüklendi uygulama etki alanı çağrısı için kullanılan [Icordebugappdomain3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99001-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99001-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99001-113">Requirements</span></span>  
 <span data-ttu-id="99001-114">**Platform:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99001-114">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="99001-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99001-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99001-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99001-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99001-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99001-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99001-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99001-118">See Also</span></span>  
 [<span data-ttu-id="99001-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="99001-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
