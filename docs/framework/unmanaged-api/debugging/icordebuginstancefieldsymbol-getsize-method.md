---
title: 'Icordebugınstancefieldsymbol:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ff0ddc266ef9a3f5fabf56f43f1eba2c74e3a8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910181"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="6ea26-102">Icordebugınstancefieldsymbol:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ea26-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="6ea26-103">Örnek alanının bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="6ea26-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ea26-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ea26-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ea26-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ea26-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="6ea26-106">dışı Alanın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6ea26-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ea26-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ea26-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ea26-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6ea26-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ea26-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ea26-109">Requirements</span></span>  
 <span data-ttu-id="6ea26-110">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ea26-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ea26-111">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6ea26-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ea26-112">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6ea26-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ea26-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ea26-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ea26-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ea26-114">See also</span></span>

- [<span data-ttu-id="6ea26-115">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ea26-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="6ea26-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6ea26-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
