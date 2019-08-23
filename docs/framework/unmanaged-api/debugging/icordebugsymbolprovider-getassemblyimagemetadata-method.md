---
title: 'ICorDebugSymbolProvider:: Getassemblyımagemetadata yöntemi'
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad86c42d0f23de25fe0e5b9123a0dba3695d8d64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964653"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="b989a-102">ICorDebugSymbolProvider:: Getassemblyımagemetadata yöntemi</span><span class="sxs-lookup"><span data-stu-id="b989a-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="b989a-103">Birleştirilmiş bir derlemeden meta verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="b989a-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b989a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b989a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b989a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b989a-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="b989a-106">dışı Birleştirilmiş derlemenin meta verilerinin boyut ve adresi hakkında bilgi içeren bir [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b989a-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b989a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b989a-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b989a-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b989a-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b989a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b989a-109">Requirements</span></span>  
 <span data-ttu-id="b989a-110">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b989a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b989a-111">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b989a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b989a-112">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b989a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b989a-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b989a-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b989a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b989a-114">See also</span></span>

- [<span data-ttu-id="b989a-115">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b989a-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="b989a-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b989a-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
