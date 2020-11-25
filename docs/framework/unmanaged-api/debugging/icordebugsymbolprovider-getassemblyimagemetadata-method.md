---
title: 'ICorDebugSymbolProvider:: Getassemblyımagemetadata yöntemi'
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
ms.openlocfilehash: 9644d1323660730d210bd0305c2785fce4174455
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709147"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="03640-102">ICorDebugSymbolProvider:: Getassemblyımagemetadata yöntemi</span><span class="sxs-lookup"><span data-stu-id="03640-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>

<span data-ttu-id="03640-103">Birleştirilmiş bir derlemeden meta verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="03640-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03640-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="03640-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03640-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03640-105">Parameters</span></span>  

 `ppMemoryBuffer`  
 <span data-ttu-id="03640-106">dışı Birleştirilmiş derlemenin meta verilerinin boyut ve adresi hakkında bilgi içeren bir [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="03640-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03640-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03640-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03640-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="03640-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03640-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03640-109">Requirements</span></span>  

 <span data-ttu-id="03640-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03640-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03640-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="03640-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03640-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="03640-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03640-113">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03640-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03640-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03640-114">See also</span></span>

- [<span data-ttu-id="03640-115">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03640-115">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="03640-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="03640-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
