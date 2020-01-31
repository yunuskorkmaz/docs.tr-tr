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
ms.openlocfilehash: 1ec54f4fe36aaf38d7c0ce0586733729bd2fddea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784462"
---
# <a name="icordebugboxvalue-interface"></a><span data-ttu-id="f5a17-102">ICorDebugBoxValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5a17-102">ICorDebugBoxValue Interface</span></span>

<span data-ttu-id="f5a17-103">Kutulanmış değer sınıf nesnesini temsil eden "ICorDebugHeapValue" öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f5a17-103">A subclass of "ICorDebugHeapValue" that represents a boxed value class object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5a17-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f5a17-104">Methods</span></span>  
  
|<span data-ttu-id="f5a17-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f5a17-105">Method</span></span>|<span data-ttu-id="f5a17-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5a17-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f5a17-107">GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5a17-107">GetObject Method</span></span>](icordebugboxvalue-getobject-method.md)|<span data-ttu-id="f5a17-108">Kutulanmış "ICorDebugObjectValue" örneğine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="f5a17-108">Gets an interface pointer to the boxed "ICorDebugObjectValue" instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5a17-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5a17-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5a17-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="f5a17-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5a17-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5a17-111">Requirements</span></span>  
 <span data-ttu-id="f5a17-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5a17-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5a17-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f5a17-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5a17-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f5a17-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5a17-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5a17-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5a17-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5a17-116">See also</span></span>

- [<span data-ttu-id="f5a17-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f5a17-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
