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
ms.openlocfilehash: da921644c4d967efb0d88060ada0332c5eb63965
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138526"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="73dce-102">ICorDebugGuidToTypeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73dce-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="73dce-103">ICorDebugType örnekleri tarafından temsil edilen bir GUID kümesi ve bunlara karşılık gelen türleri arasındaki eşlemeyi tanımlayan bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="73dce-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="73dce-104">Bu arabirim, ıcorıcertificate Genum arabiriminden gelen yöntemleri devralır.</span><span class="sxs-lookup"><span data-stu-id="73dce-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73dce-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="73dce-105">Methods</span></span>  
  
|<span data-ttu-id="73dce-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="73dce-106">Method</span></span>|<span data-ttu-id="73dce-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73dce-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73dce-108">ICorDebugGuidToTypeEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="73dce-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="73dce-109">GUID 'Leri tür bilgilerine eşleyen, belirtilen [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="73dce-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73dce-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73dce-110">Remarks</span></span>  
 <span data-ttu-id="73dce-111">[ICorDebugAppDomain3:: GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) yöntemi çağırarak bir `ICorDebugGuidToTypeEnum` arabirimi nesnesi alınabilir.</span><span class="sxs-lookup"><span data-stu-id="73dce-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="73dce-112">Bir hata ayıklayıcı, [](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) [](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) [Bu arabirimin bir sonraki yöntemini çağırmak için kullanılan uygulama etki alanında yüklü Windows çalışma zamanı türlerinin yönetilen gösterimlerinden eşlemelerini temsil eden CorDebugGuidToTypeMapping nesneleri elde edebilir. ICorDebugAppDomain3:: Getcachedwınrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metodu.</span><span class="sxs-lookup"><span data-stu-id="73dce-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73dce-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73dce-113">Requirements</span></span>  
 <span data-ttu-id="73dce-114">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="73dce-114">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="73dce-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="73dce-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73dce-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="73dce-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73dce-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73dce-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73dce-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73dce-118">See also</span></span>

- [<span data-ttu-id="73dce-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="73dce-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
