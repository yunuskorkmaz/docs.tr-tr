---
title: 'ICorDebugStaticFieldSymbol:: GetAddress Yöntemi'
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: 65761e48491b2a4c81ccd05b17d8723f71f52e5c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131791"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="3e35b-102">ICorDebugStaticFieldSymbol:: GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e35b-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="3e35b-103">Statik bir alanın adresini alır.</span><span class="sxs-lookup"><span data-stu-id="3e35b-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e35b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e35b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e35b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3e35b-105">Parameters</span></span>  
 <span data-ttu-id="3e35b-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="3e35b-106">pRVA</span></span>  
 <span data-ttu-id="3e35b-107">dışı Statik alanın göreli sanal adresine (RVA) yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3e35b-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e35b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e35b-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e35b-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3e35b-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e35b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e35b-110">Requirements</span></span>  
 <span data-ttu-id="3e35b-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e35b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e35b-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3e35b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e35b-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3e35b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e35b-114">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e35b-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e35b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e35b-115">See also</span></span>

- [<span data-ttu-id="3e35b-116">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e35b-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="3e35b-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3e35b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
