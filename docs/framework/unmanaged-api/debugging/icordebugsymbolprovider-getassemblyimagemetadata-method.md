---
title: "ICorDebugSymbolProvider::GetAssemblyImageMetadata yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 48e5e9daf191cb2f4112dd2a957f29c0a7521398
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="1e018-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e018-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="1e018-103">Birleştirilmiş bir derlemeye ait meta verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e018-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e018-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e018-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1e018-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e018-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="1e018-106">[out] Adresine bir işaretçi bir [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) boyutunu ve birleştirilmiş derlemenin meta verilerini adresini hakkında bilgi içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="1e018-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e018-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e018-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e018-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1e018-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e018-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e018-109">Requirements</span></span>  
 <span data-ttu-id="1e018-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e018-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e018-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e018-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e018-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e018-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e018-113">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e018-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e018-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e018-114">See Also</span></span>  
 [<span data-ttu-id="1e018-115">ICorDebugSymbolProvider arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e018-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="1e018-116">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1e018-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
