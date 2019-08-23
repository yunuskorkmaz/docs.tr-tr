---
title: 'Icordebugınstancefieldsymbol:: GetOffset Yöntemi'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 453f691f414050905f5d73e201ebeed79e2aaf50
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910199"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="518e6-102">Icordebugınstancefieldsymbol:: GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="518e6-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="518e6-103">Üst sınıfındaki bu örnek alanının bayt cinsinden konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="518e6-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="518e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="518e6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="518e6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="518e6-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="518e6-106">Bu örnek alanın üst sınıfında kaydırılacağı bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="518e6-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="518e6-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="518e6-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="518e6-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="518e6-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="518e6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="518e6-109">Requirements</span></span>  
 <span data-ttu-id="518e6-110">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="518e6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="518e6-111">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="518e6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="518e6-112">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="518e6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="518e6-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="518e6-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="518e6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="518e6-114">See also</span></span>

- [<span data-ttu-id="518e6-115">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="518e6-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="518e6-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="518e6-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
