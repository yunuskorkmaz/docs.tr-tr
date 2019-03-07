---
title: ICorDebugLoadedModule::GetBaseAddress Metodu
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31b398080c1355441a35871d0685283783efcd52
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501234"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="0303b-102">ICorDebugLoadedModule::GetBaseAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="0303b-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="0303b-103">Yüklenen bir modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="0303b-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0303b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0303b-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0303b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0303b-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="0303b-106">[out] Yüklenen bir modülün taban adresi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0303b-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0303b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0303b-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0303b-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0303b-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0303b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0303b-109">Requirements</span></span>  
 <span data-ttu-id="0303b-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0303b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0303b-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0303b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0303b-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0303b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0303b-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0303b-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0303b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0303b-114">See also</span></span>
- [<span data-ttu-id="0303b-115">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0303b-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="0303b-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0303b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
