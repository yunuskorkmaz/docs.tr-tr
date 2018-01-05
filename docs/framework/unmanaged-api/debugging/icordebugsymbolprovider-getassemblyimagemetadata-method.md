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
ms.workload: dotnet
ms.openlocfilehash: ff6b26dd9a0ed56e5194dc997270cf9d2dbe42b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="951cd-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata yöntemi</span><span class="sxs-lookup"><span data-stu-id="951cd-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="951cd-103">Birleştirilmiş bir derlemeye ait meta verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="951cd-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="951cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="951cd-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="951cd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="951cd-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="951cd-106">[out] Adresine bir işaretçi bir [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) boyutunu ve birleştirilmiş derlemenin meta verilerini adresini hakkında bilgi içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="951cd-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="951cd-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="951cd-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="951cd-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="951cd-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="951cd-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="951cd-109">Requirements</span></span>  
 <span data-ttu-id="951cd-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="951cd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="951cd-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="951cd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="951cd-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="951cd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="951cd-113">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="951cd-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="951cd-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="951cd-114">See Also</span></span>  
 [<span data-ttu-id="951cd-115">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="951cd-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="951cd-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="951cd-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
