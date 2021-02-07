---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugDataTarget3:: GetLoadedModules yöntemi'
title: ICorDebugDataTarget3::GetLoadedModules Yöntemi
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: ea6350155fd79b52a37133cad95f624635433a3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764352"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="618f2-103">ICorDebugDataTarget3::GetLoadedModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="618f2-103">ICorDebugDataTarget3::GetLoadedModules Method</span></span>

<span data-ttu-id="618f2-104">Şimdiye kadar yüklenmiş modüllerin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="618f2-104">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="618f2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="618f2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="618f2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="618f2-106">Parameters</span></span>  

 `cRequestedModules`  
 <span data-ttu-id="618f2-107">'ndaki Bilgilerin istendiği modül sayısı.</span><span class="sxs-lookup"><span data-stu-id="618f2-107">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="618f2-108">dışı Bilgilerin döndürüldüğü modül sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="618f2-108">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="618f2-109">dışı Yüklü modüller hakkında bilgi sağlayan [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) nesneleri dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="618f2-109">[out] A pointer to an array of [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="618f2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="618f2-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="618f2-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="618f2-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="618f2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="618f2-112">Requirements</span></span>  

 <span data-ttu-id="618f2-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="618f2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="618f2-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="618f2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="618f2-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="618f2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="618f2-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="618f2-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="618f2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="618f2-117">See also</span></span>

- [<span data-ttu-id="618f2-118">ICorDebugDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="618f2-118">ICorDebugDataTarget3 Interface</span></span>](icordebugdatatarget3-interface.md)
- [<span data-ttu-id="618f2-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="618f2-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
