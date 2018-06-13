---
title: ICorDebugLoadedModule::GetSize Metodu
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9768fb91749158bf3193919b2106bde1c618468a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413237"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="cb3ec-102">ICorDebugLoadedModule::GetSize Metodu</span><span class="sxs-lookup"><span data-stu-id="cb3ec-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="cb3ec-103">Yüklenen modülün bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="cb3ec-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb3ec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb3ec-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb3ec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb3ec-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="cb3ec-106">[out] Yüklenen modülün bayt sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cb3ec-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb3ec-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb3ec-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb3ec-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cb3ec-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb3ec-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb3ec-109">Requirements</span></span>  
 <span data-ttu-id="cb3ec-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb3ec-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb3ec-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb3ec-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb3ec-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb3ec-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb3ec-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb3ec-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb3ec-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb3ec-114">See Also</span></span>  
 [<span data-ttu-id="cb3ec-115">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb3ec-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="cb3ec-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cb3ec-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
