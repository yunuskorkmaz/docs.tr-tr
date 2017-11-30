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
ms.openlocfilehash: 29adc45df57c5f31c299dc28b611bcf0599d4aac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="e9b4b-102">ICorDebugLoadedModule::GetSize Metodu</span><span class="sxs-lookup"><span data-stu-id="e9b4b-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="e9b4b-103">Yüklenen modülün bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="e9b4b-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9b4b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9b4b-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9b4b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9b4b-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="e9b4b-106">[out] Yüklenen modülün bayt sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e9b4b-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9b4b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9b4b-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9b4b-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9b4b-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9b4b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9b4b-109">Requirements</span></span>  
 <span data-ttu-id="e9b4b-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9b4b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9b4b-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9b4b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9b4b-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9b4b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9b4b-113">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9b4b-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9b4b-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9b4b-114">See Also</span></span>  
 [<span data-ttu-id="e9b4b-115">Icordebugloadedmodule arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9b4b-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="e9b4b-116">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e9b4b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
