---
description: ': ICorDebugStaticFieldSymbol:: GetAddress yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugStaticFieldSymbol:: GetAddress Yöntemi'
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: 1944839ff6afc31dc3667111397cbb088b95b412
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801013"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="a34a7-103">ICorDebugStaticFieldSymbol:: GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a34a7-103">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>

<span data-ttu-id="a34a7-104">Statik bir alanın adresini alır.</span><span class="sxs-lookup"><span data-stu-id="a34a7-104">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a34a7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a34a7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a34a7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a34a7-106">Parameters</span></span>  

 <span data-ttu-id="a34a7-107">pRVA</span><span class="sxs-lookup"><span data-stu-id="a34a7-107">pRVA</span></span>  
 <span data-ttu-id="a34a7-108">dışı Statik alanın göreli sanal adresine (RVA) yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a34a7-108">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a34a7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a34a7-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a34a7-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a34a7-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a34a7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a34a7-111">Requirements</span></span>  

 <span data-ttu-id="a34a7-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a34a7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a34a7-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a34a7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a34a7-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a34a7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a34a7-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a34a7-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a34a7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a34a7-116">See also</span></span>

- [<span data-ttu-id="a34a7-117">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a34a7-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="a34a7-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a34a7-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
