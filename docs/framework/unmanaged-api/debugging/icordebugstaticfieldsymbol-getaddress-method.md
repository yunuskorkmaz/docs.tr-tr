---
title: ICorDebugStaticFieldSymbol::GetAddress yöntemi
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e233fe78f6b2c721114f0307a8ca414625a0087e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782648"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="6e7d9-102">ICorDebugStaticFieldSymbol::GetAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e7d9-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="6e7d9-103">Statik alan adresini alır.</span><span class="sxs-lookup"><span data-stu-id="6e7d9-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e7d9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e7d9-104">Syntax</span></span>  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e7d9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e7d9-105">Parameters</span></span>  
 <span data-ttu-id="6e7d9-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="6e7d9-106">pRVA</span></span>  
 <span data-ttu-id="6e7d9-107">[out] Statik alan göreli sanal adres (RVA) için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6e7d9-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e7d9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e7d9-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e7d9-109">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e7d9-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e7d9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e7d9-110">Requirements</span></span>  
 <span data-ttu-id="6e7d9-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e7d9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e7d9-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e7d9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e7d9-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e7d9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e7d9-114">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e7d9-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e7d9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e7d9-115">See also</span></span>

- [<span data-ttu-id="6e7d9-116">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e7d9-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="6e7d9-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6e7d9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
