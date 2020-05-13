---
title: 'ICorDebugStaticFieldSymbol:: GetAddress Yöntemi'
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: 7b8072234df172eeafd77db90287ea3319c08ec7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378762"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="e2a63-102">ICorDebugStaticFieldSymbol:: GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2a63-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="e2a63-103">Statik bir alanın adresini alır.</span><span class="sxs-lookup"><span data-stu-id="e2a63-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2a63-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2a63-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2a63-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2a63-105">Parameters</span></span>  
 <span data-ttu-id="e2a63-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="e2a63-106">pRVA</span></span>  
 <span data-ttu-id="e2a63-107">dışı Statik alanın göreli sanal adresine (RVA) yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2a63-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2a63-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2a63-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2a63-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2a63-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2a63-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2a63-110">Requirements</span></span>  
 <span data-ttu-id="e2a63-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2a63-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2a63-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e2a63-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2a63-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e2a63-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2a63-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2a63-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2a63-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2a63-115">See also</span></span>

- [<span data-ttu-id="e2a63-116">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2a63-116">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="e2a63-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e2a63-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
