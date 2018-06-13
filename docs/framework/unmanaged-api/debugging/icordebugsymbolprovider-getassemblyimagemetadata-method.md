---
title: ICorDebugSymbolProvider::GetAssemblyImageMetadata yöntemi
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bf032f3bf525d2dca535e6f62dd65d5acd8e7f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420995"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="abb0a-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata yöntemi</span><span class="sxs-lookup"><span data-stu-id="abb0a-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="abb0a-103">Birleştirilmiş bir derlemeye ait meta verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="abb0a-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abb0a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abb0a-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abb0a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="abb0a-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="abb0a-106">[out] Adresine bir işaretçi bir [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) boyutunu ve birleştirilmiş derlemenin meta verilerini adresini hakkında bilgi içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="abb0a-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abb0a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="abb0a-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abb0a-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="abb0a-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abb0a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="abb0a-109">Requirements</span></span>  
 <span data-ttu-id="abb0a-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abb0a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abb0a-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abb0a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abb0a-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abb0a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abb0a-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abb0a-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abb0a-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="abb0a-114">See Also</span></span>  
 [<span data-ttu-id="abb0a-115">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abb0a-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="abb0a-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="abb0a-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
