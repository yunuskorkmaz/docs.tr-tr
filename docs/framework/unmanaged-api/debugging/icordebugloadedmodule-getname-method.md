---
title: ICorDebugLoadedModule::GetName Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aee475dfc425eea32ce4a1e5b4a081593574ba64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="5b56e-102">ICorDebugLoadedModule::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="5b56e-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="5b56e-103">Yüklenen modül adını alır.</span><span class="sxs-lookup"><span data-stu-id="5b56e-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b56e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b56e-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b56e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5b56e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="5b56e-106">[in] Karakter sayısını `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="5b56e-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5b56e-107">[out] Gerçekte yazılan karakter sayısını gösteren bir işaretçi `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="5b56e-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="5b56e-108">[out] Yüklenen modülünün adını içeren karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="5b56e-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b56e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b56e-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b56e-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b56e-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b56e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b56e-111">Requirements</span></span>  
 <span data-ttu-id="5b56e-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b56e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b56e-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b56e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b56e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b56e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b56e-115">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b56e-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b56e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5b56e-116">See Also</span></span>  
 [<span data-ttu-id="5b56e-117">Icordebugloadedmodule arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b56e-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="5b56e-118">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5b56e-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
