---
title: ICorDebugLoadedModule::GetBaseAddress Metodu
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5ef73be22ea79d15ec53e8ab33c34441002acce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732433"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="17a50-102">ICorDebugLoadedModule::GetBaseAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="17a50-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="17a50-103">Yüklenen bir modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="17a50-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17a50-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17a50-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17a50-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17a50-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="17a50-106">[out] Yüklenen bir modülün taban adresi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="17a50-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17a50-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17a50-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17a50-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="17a50-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17a50-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17a50-109">Requirements</span></span>  
 <span data-ttu-id="17a50-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17a50-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17a50-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17a50-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17a50-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17a50-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17a50-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17a50-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17a50-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17a50-114">See also</span></span>
- [<span data-ttu-id="17a50-115">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17a50-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="17a50-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="17a50-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
