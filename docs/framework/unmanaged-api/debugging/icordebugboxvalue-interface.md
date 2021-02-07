---
description: ': ICorDebugBoxValue Arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 86a985d3cbb8330efdef1d6636f91b64c3f78bc6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711940"
---
# <a name="icordebugboxvalue-interface"></a><span data-ttu-id="49ff0-103">ICorDebugBoxValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49ff0-103">ICorDebugBoxValue Interface</span></span>

<span data-ttu-id="49ff0-104">Kutulanmış değer sınıf nesnesini temsil eden "ICorDebugHeapValue" öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="49ff0-104">A subclass of "ICorDebugHeapValue" that represents a boxed value class object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="49ff0-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="49ff0-105">Methods</span></span>  
  
|<span data-ttu-id="49ff0-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="49ff0-106">Method</span></span>|<span data-ttu-id="49ff0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49ff0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="49ff0-108">GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="49ff0-108">GetObject Method</span></span>](icordebugboxvalue-getobject-method.md)|<span data-ttu-id="49ff0-109">Kutulanmış "ICorDebugObjectValue" örneğine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="49ff0-109">Gets an interface pointer to the boxed "ICorDebugObjectValue" instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49ff0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49ff0-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49ff0-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="49ff0-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49ff0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49ff0-112">Requirements</span></span>  

 <span data-ttu-id="49ff0-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49ff0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49ff0-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="49ff0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49ff0-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="49ff0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49ff0-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49ff0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49ff0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49ff0-117">See also</span></span>

- [<span data-ttu-id="49ff0-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="49ff0-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
