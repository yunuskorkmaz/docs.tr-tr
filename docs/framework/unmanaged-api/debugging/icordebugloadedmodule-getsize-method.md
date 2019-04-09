---
title: ICorDebugLoadedModule::GetSize Metodu
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4601261971cce32b6d6d9ee7377f725a85103a1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183475"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="00f1e-102">ICorDebugLoadedModule::GetSize Metodu</span><span class="sxs-lookup"><span data-stu-id="00f1e-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="00f1e-103">Yüklenen bir modülün bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="00f1e-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00f1e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00f1e-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00f1e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="00f1e-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="00f1e-106">[out] Yüklenen bir modülün bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="00f1e-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00f1e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00f1e-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00f1e-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="00f1e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00f1e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00f1e-109">Requirements</span></span>  
 <span data-ttu-id="00f1e-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00f1e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00f1e-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00f1e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00f1e-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00f1e-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="00f1e-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="00f1e-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="00f1e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00f1e-114">See also</span></span>

- [<span data-ttu-id="00f1e-115">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00f1e-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="00f1e-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="00f1e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
