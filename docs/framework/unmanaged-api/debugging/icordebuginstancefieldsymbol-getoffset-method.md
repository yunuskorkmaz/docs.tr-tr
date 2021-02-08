---
description: ': Icordebugınstancefieldsymbol:: GetOffset Yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugınstancefieldsymbol:: GetOffset Yöntemi'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 4a877b2f78adfac5c54694ab306fd7db60f266f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791172"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="4e354-103">Icordebugınstancefieldsymbol:: GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e354-103">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>

<span data-ttu-id="4e354-104">Üst sınıfındaki bu örnek alanının bayt cinsinden konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="4e354-104">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e354-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e354-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e354-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e354-106">Parameters</span></span>  

 `pcbOffset`  
 <span data-ttu-id="4e354-107">Bu örnek alanın üst sınıfında kaydırılacağı bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4e354-107">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e354-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e354-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e354-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4e354-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e354-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e354-110">Requirements</span></span>  

 <span data-ttu-id="4e354-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e354-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e354-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4e354-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e354-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4e354-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e354-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e354-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e354-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e354-115">See also</span></span>

- [<span data-ttu-id="4e354-116">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e354-116">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="4e354-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4e354-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
