---
title: ICorDebugLoadedModule::GetSize Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fb340845afac0f5a13f7c4646d11ac057ebd054
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="33ccf-102">ICorDebugLoadedModule::GetSize Metodu</span><span class="sxs-lookup"><span data-stu-id="33ccf-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="33ccf-103">Yüklenen modülün bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="33ccf-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33ccf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33ccf-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33ccf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="33ccf-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="33ccf-106">[out] Yüklenen modülün bayt sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="33ccf-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33ccf-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33ccf-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33ccf-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33ccf-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33ccf-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33ccf-109">Requirements</span></span>  
 <span data-ttu-id="33ccf-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33ccf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33ccf-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33ccf-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33ccf-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33ccf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33ccf-113">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33ccf-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33ccf-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="33ccf-114">See Also</span></span>  
 [<span data-ttu-id="33ccf-115">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33ccf-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="33ccf-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="33ccf-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
