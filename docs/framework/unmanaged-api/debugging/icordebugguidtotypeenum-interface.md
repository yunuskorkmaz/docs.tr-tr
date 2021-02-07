---
description: ': ICorDebugGuidToTypeEnum arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: abcdc9537f6f6ff2e0ac9b2be86734efbf303493
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660992"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="bf49c-103">ICorDebugGuidToTypeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf49c-103">ICorDebugGuidToTypeEnum Interface</span></span>

<span data-ttu-id="bf49c-104">ICorDebugType örnekleri tarafından temsil edilen bir GUID kümesi ve bunlara karşılık gelen türleri arasındaki eşlemeyi tanımlayan bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf49c-104">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="bf49c-105">Bu arabirim, ıcorıcertificate Genum arabiriminden gelen yöntemleri devralır.</span><span class="sxs-lookup"><span data-stu-id="bf49c-105">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf49c-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bf49c-106">Methods</span></span>  
  
|<span data-ttu-id="bf49c-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bf49c-107">Method</span></span>|<span data-ttu-id="bf49c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf49c-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bf49c-109">ICorDebugGuidToTypeEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="bf49c-109">ICorDebugGuidToTypeEnum::Next</span></span>](icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="bf49c-110">GUID 'Leri tür bilgilerine eşleyen, belirtilen [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="bf49c-110">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf49c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf49c-111">Remarks</span></span>  

 <span data-ttu-id="bf49c-112">Bir `ICorDebugGuidToTypeEnum` arabirim nesnesi, [ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) yöntemi çağırarak alınabilir.</span><span class="sxs-lookup"><span data-stu-id="bf49c-112">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="bf49c-113">Bir hata ayıklayıcı, [ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) yöntemine yapılan çağrı için kullanılan uygulama etki alanında yüklü Windows çalışma zamanı türlerinin yönetilen gösterimlerinden eşlemelerini temsil eden [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) nesnelerini almak için bu arabirimin [sonraki](icordebugguidtotypeenum-next-method.md) metodunu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="bf49c-113">A debugger can call this interface's [Next](icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf49c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf49c-114">Requirements</span></span>  

 <span data-ttu-id="bf49c-115">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="bf49c-115">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="bf49c-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bf49c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf49c-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bf49c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf49c-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf49c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf49c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf49c-119">See also</span></span>

- [<span data-ttu-id="bf49c-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bf49c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
