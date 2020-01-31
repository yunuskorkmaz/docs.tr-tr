---
title: 'ICorDebugStaticFieldSymbol:: GetAddress Yöntemi'
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: be4d59fe668026c4b40be4c6d0afcf718c8157bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791841"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="44e3c-102">ICorDebugStaticFieldSymbol:: GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="44e3c-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="44e3c-103">Statik bir alanın adresini alır.</span><span class="sxs-lookup"><span data-stu-id="44e3c-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44e3c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44e3c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44e3c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="44e3c-105">Parameters</span></span>  
 <span data-ttu-id="44e3c-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="44e3c-106">pRVA</span></span>  
 <span data-ttu-id="44e3c-107">dışı Statik alanın göreli sanal adresine (RVA) yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="44e3c-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44e3c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44e3c-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="44e3c-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="44e3c-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44e3c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44e3c-110">Requirements</span></span>  
 <span data-ttu-id="44e3c-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44e3c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44e3c-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="44e3c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44e3c-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="44e3c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44e3c-114">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44e3c-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e3c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44e3c-115">See also</span></span>

- [<span data-ttu-id="44e3c-116">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44e3c-116">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="44e3c-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="44e3c-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
