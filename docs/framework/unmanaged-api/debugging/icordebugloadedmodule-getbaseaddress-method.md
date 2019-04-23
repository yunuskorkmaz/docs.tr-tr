---
title: ICorDebugLoadedModule::GetBaseAddress Metodu
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e84d6deca0cd09cc547636007208c70ab91c1ab1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223543"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="a3079-102">ICorDebugLoadedModule::GetBaseAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="a3079-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="a3079-103">Yüklenen bir modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="a3079-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3079-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3079-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3079-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3079-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="a3079-106">[out] Yüklenen bir modülün taban adresi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a3079-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3079-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3079-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3079-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a3079-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3079-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3079-109">Requirements</span></span>  
 <span data-ttu-id="a3079-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3079-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3079-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3079-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3079-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3079-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3079-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3079-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3079-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3079-114">See also</span></span>

- [<span data-ttu-id="a3079-115">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3079-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="a3079-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a3079-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
