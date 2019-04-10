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
ms.openlocfilehash: f2ea67c6e4d860d41cfe67aaab73babb51f3ce45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210665"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="1569c-102">ICorDebugGuidToTypeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1569c-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="1569c-103">Icordebugtype örnekleri tarafından temsil edilen bunların karşılık gelen türlerine ve GUID'leri kümesi arasındaki eşlemeyi tanımlar bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1569c-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="1569c-104">Bu arabirim yöntemleri Icordebugenum arabirimi devralır.</span><span class="sxs-lookup"><span data-stu-id="1569c-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1569c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1569c-105">Methods</span></span>  
  
|<span data-ttu-id="1569c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1569c-106">Method</span></span>|<span data-ttu-id="1569c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1569c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1569c-108">Icordebugguidtotypeenum::Next</span><span class="sxs-lookup"><span data-stu-id="1569c-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="1569c-109">Belirtilen sayıda alır [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) bilgi GUID'leri harita örneği.</span><span class="sxs-lookup"><span data-stu-id="1569c-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1569c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1569c-110">Remarks</span></span>  
 <span data-ttu-id="1569c-111">Bir `ICorDebugGuidToTypeEnum` arabirimi nesnesi çağrılarak alınabilir [Icordebugappdomain3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1569c-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="1569c-112">Bir hata ayıklayıcı bu arabirimi çağırabilir [sonraki](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) alınacak yöntemi [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) eşleşmelerini temsil eden nesneleri yönetilen temsillerini [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türleri yüklenen içinde uygulama etki alanı için yapılan çağrının kullanılan [Icordebugappdomain3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1569c-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1569c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1569c-113">Requirements</span></span>  
 **<span data-ttu-id="1569c-114">Platformlar:</span><span class="sxs-lookup"><span data-stu-id="1569c-114">Platforms:</span></span>** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 <span data-ttu-id="1569c-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1569c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1569c-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1569c-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1569c-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="1569c-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1569c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1569c-118">See also</span></span>

- [<span data-ttu-id="1569c-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1569c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
