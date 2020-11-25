---
title: ICorDebugDataTarget3::GetLoadedModules Yöntemi
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: efbada02b7a24e0a7ed613b86b8a4a1a0b5b051a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713760"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="7598d-102">ICorDebugDataTarget3::GetLoadedModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7598d-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>

<span data-ttu-id="7598d-103">Şimdiye kadar yüklenmiş modüllerin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="7598d-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7598d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7598d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7598d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7598d-105">Parameters</span></span>  

 `cRequestedModules`  
 <span data-ttu-id="7598d-106">'ndaki Bilgilerin istendiği modül sayısı.</span><span class="sxs-lookup"><span data-stu-id="7598d-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="7598d-107">dışı Bilgilerin döndürüldüğü modül sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7598d-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="7598d-108">dışı Yüklü modüller hakkında bilgi sağlayan [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) nesneleri dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7598d-108">[out] A pointer to an array of [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7598d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7598d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7598d-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7598d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7598d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7598d-111">Requirements</span></span>  

 <span data-ttu-id="7598d-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7598d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7598d-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7598d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7598d-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7598d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7598d-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7598d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7598d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7598d-116">See also</span></span>

- [<span data-ttu-id="7598d-117">ICorDebugDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7598d-117">ICorDebugDataTarget3 Interface</span></span>](icordebugdatatarget3-interface.md)
- [<span data-ttu-id="7598d-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7598d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
