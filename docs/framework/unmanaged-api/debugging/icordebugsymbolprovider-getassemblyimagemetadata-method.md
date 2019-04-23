---
title: ICorDebugSymbolProvider::GetAssemblyImageMetadata yöntemi
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0be0722db374ff49541b3c4b68f295774f34163e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104136"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="9d7da-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d7da-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="9d7da-103">Birleştirilmiş bir derlemesinden meta verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="9d7da-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d7da-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d7da-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d7da-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d7da-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="9d7da-106">[out] Adresine bir işaretçi bir [Icordebugmemorybuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) boyutu ve birleştirilmiş bir derlemenin meta verilerini adresi hakkında bilgi içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="9d7da-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d7da-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d7da-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d7da-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d7da-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d7da-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d7da-109">Requirements</span></span>  
 <span data-ttu-id="9d7da-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d7da-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d7da-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d7da-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d7da-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d7da-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d7da-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d7da-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d7da-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d7da-114">See also</span></span>

- [<span data-ttu-id="9d7da-115">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d7da-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="9d7da-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9d7da-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
