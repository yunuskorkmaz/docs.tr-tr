---
title: Icordebugobjectenum arabirimi1
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a9f10301db488e4ca68ce5fdaf0ba767053d7d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547007"
---
# <a name="icordebugobjectenum-interface1"></a><span data-ttu-id="ebcef-102">Icordebugobjectenum arabirimi1</span><span class="sxs-lookup"><span data-stu-id="ebcef-102">ICorDebugObjectEnum Interface1</span></span>
<span data-ttu-id="ebcef-103">Icordebugenum yöntemlerini uygular ve bunların göreli sanal adreslerine (RVA) göre nesne dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="ebcef-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ebcef-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ebcef-104">Methods</span></span>  
  
|<span data-ttu-id="ebcef-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ebcef-105">Method</span></span>|<span data-ttu-id="ebcef-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ebcef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ebcef-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebcef-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="ebcef-108">RVA belirli sayıda nesneleri, geçerli konumdan başlayarak sabit listesi alır.</span><span class="sxs-lookup"><span data-stu-id="ebcef-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebcef-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ebcef-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebcef-110">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ebcef-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebcef-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebcef-111">Requirements</span></span>  
 <span data-ttu-id="ebcef-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebcef-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebcef-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ebcef-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebcef-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebcef-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebcef-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebcef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebcef-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebcef-116">See also</span></span>
- [<span data-ttu-id="ebcef-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ebcef-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
