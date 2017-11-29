---
title: ICorDebugLoadedModule::GetBaseAddress Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b192c606697896371202e98945f83623bbb99bb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="88cc2-102">ICorDebugLoadedModule::GetBaseAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="88cc2-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="88cc2-103">Yüklenen modülün taban adresi alır.</span><span class="sxs-lookup"><span data-stu-id="88cc2-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88cc2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88cc2-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88cc2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88cc2-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="88cc2-106">[out] Yüklenen modülün temel adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="88cc2-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88cc2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88cc2-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88cc2-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="88cc2-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88cc2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88cc2-109">Requirements</span></span>  
 <span data-ttu-id="88cc2-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88cc2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88cc2-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88cc2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88cc2-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88cc2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88cc2-113">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88cc2-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88cc2-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88cc2-114">See Also</span></span>  
 [<span data-ttu-id="88cc2-115">Icordebugloadedmodule arabirimi</span><span class="sxs-lookup"><span data-stu-id="88cc2-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="88cc2-116">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="88cc2-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
