---
title: ICorDebugDataTarget3::GetLoadedModules Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc4820d2c71830b297ed690c440c90cfff1f9601
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="9b770-102">ICorDebugDataTarget3::GetLoadedModules Metodu</span><span class="sxs-lookup"><span data-stu-id="9b770-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="9b770-103">Şu ana kadar yüklü modüllerin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="9b770-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b770-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b770-104">Syntax</span></span>  
  
```  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b770-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b770-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="9b770-106">[in] İstenen bilgilerin için modülleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="9b770-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="9b770-107">[out] Modüller hakkında bilgisi döndürülmedi sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9b770-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="9b770-108">[out] Bir dizi için bir işaretçi [Icordebugloadedmodule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) hakkında bilgi sağlayan nesneleri yüklenen modüller.</span><span class="sxs-lookup"><span data-stu-id="9b770-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b770-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b770-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b770-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9b770-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b770-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b770-111">Requirements</span></span>  
 <span data-ttu-id="9b770-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b770-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b770-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b770-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b770-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b770-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b770-115">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b770-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b770-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b770-116">See Also</span></span>  
 [<span data-ttu-id="9b770-117">Icordebugdatatarget3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b770-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 [<span data-ttu-id="9b770-118">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9b770-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
