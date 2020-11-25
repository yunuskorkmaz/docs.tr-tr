---
title: ICorDebugBoxValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue
helpviewer_keywords:
- ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3d3ae7e2-97d4-46de-a2c3-cb78f3490f9d
topic_type:
- apiref
ms.openlocfilehash: 6d58ae048382a78c422703d5c6caeb3bbc739849
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723174"
---
# <a name="icordebugboxvalue-interface"></a><span data-ttu-id="ba4ef-102">ICorDebugBoxValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba4ef-102">ICorDebugBoxValue Interface</span></span>

<span data-ttu-id="ba4ef-103">Kutulanmış değer sınıf nesnesini temsil eden "ICorDebugHeapValue" öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ba4ef-103">A subclass of "ICorDebugHeapValue" that represents a boxed value class object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ba4ef-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ba4ef-104">Methods</span></span>  
  
|<span data-ttu-id="ba4ef-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ba4ef-105">Method</span></span>|<span data-ttu-id="ba4ef-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba4ef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ba4ef-107">GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="ba4ef-107">GetObject Method</span></span>](icordebugboxvalue-getobject-method.md)|<span data-ttu-id="ba4ef-108">Kutulanmış "ICorDebugObjectValue" örneğine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ba4ef-108">Gets an interface pointer to the boxed "ICorDebugObjectValue" instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba4ef-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba4ef-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ba4ef-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="ba4ef-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba4ef-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba4ef-111">Requirements</span></span>  

 <span data-ttu-id="ba4ef-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba4ef-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba4ef-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ba4ef-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba4ef-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ba4ef-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba4ef-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba4ef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba4ef-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba4ef-116">See also</span></span>

- [<span data-ttu-id="ba4ef-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ba4ef-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
