---
title: ICorDebugDataTarget3::GetLoadedModules Metodu
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b961e0a84d199f0acf22dfc0f87b1d35c118adc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651064"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="4a41b-102">ICorDebugDataTarget3::GetLoadedModules Metodu</span><span class="sxs-lookup"><span data-stu-id="4a41b-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="4a41b-103">Şu ana kadar yüklü modüllerin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="4a41b-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a41b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a41b-104">Syntax</span></span>  
  
```  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a41b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4a41b-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="4a41b-106">[in] Bilgi istendiği modül sayısı.</span><span class="sxs-lookup"><span data-stu-id="4a41b-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="4a41b-107">[out] Modüller hakkında bilgisi döndürülmedi sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4a41b-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="4a41b-108">[out] Bir dizi işaretçi [Icordebugloadedmodule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) yüklü modülleri hakkında bilgi sağlayan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="4a41b-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a41b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a41b-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a41b-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a41b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a41b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a41b-111">Requirements</span></span>  
 <span data-ttu-id="4a41b-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a41b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a41b-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a41b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a41b-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a41b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a41b-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a41b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a41b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a41b-116">See also</span></span>
- [<span data-ttu-id="4a41b-117">ICorDebugDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a41b-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)
- [<span data-ttu-id="4a41b-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4a41b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
