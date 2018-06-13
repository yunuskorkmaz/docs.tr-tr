---
title: ICorDebugLoadedModule::GetBaseAddress Metodu
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c12ea84f1a706850972b2e404ec52eea3523de7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412642"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="bca4a-102">ICorDebugLoadedModule::GetBaseAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="bca4a-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="bca4a-103">Yüklenen modülün taban adresi alır.</span><span class="sxs-lookup"><span data-stu-id="bca4a-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca4a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bca4a-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bca4a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bca4a-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="bca4a-106">[out] Yüklenen modülün temel adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bca4a-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bca4a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bca4a-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bca4a-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bca4a-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bca4a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bca4a-109">Requirements</span></span>  
 <span data-ttu-id="bca4a-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bca4a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bca4a-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bca4a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bca4a-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bca4a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bca4a-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bca4a-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca4a-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bca4a-114">See Also</span></span>  
 [<span data-ttu-id="bca4a-115">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bca4a-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="bca4a-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bca4a-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
