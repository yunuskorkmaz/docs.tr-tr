---
title: 'ICorDebugStaticFieldSymbol:: GetAddress Yöntemi'
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d41b99d7410333cb6a22443271c1fcbc41c3594
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962708"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="8fd6b-102">ICorDebugStaticFieldSymbol:: GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fd6b-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="8fd6b-103">Statik bir alanın adresini alır.</span><span class="sxs-lookup"><span data-stu-id="8fd6b-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fd6b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8fd6b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fd6b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8fd6b-105">Parameters</span></span>  
 <span data-ttu-id="8fd6b-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="8fd6b-106">pRVA</span></span>  
 <span data-ttu-id="8fd6b-107">dışı Statik alanın göreli sanal adresine (RVA) yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8fd6b-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fd6b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fd6b-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8fd6b-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8fd6b-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fd6b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8fd6b-110">Requirements</span></span>  
 <span data-ttu-id="8fd6b-111">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fd6b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fd6b-112">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8fd6b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8fd6b-113">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8fd6b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fd6b-114">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fd6b-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fd6b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fd6b-115">See also</span></span>

- [<span data-ttu-id="8fd6b-116">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8fd6b-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="8fd6b-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8fd6b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
