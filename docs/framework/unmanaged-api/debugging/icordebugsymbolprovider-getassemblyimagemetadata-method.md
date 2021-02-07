---
description: ': ICorDebugSymbolProvider:: Getassemblyımagemetadata yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugSymbolProvider:: Getassemblyımagemetadata yöntemi'
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
ms.openlocfilehash: 4abe5cc2b2a31f89e6ca4f8fc643f26eac276515
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717192"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="65c2f-103">ICorDebugSymbolProvider:: Getassemblyımagemetadata yöntemi</span><span class="sxs-lookup"><span data-stu-id="65c2f-103">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>

<span data-ttu-id="65c2f-104">Birleştirilmiş bir derlemeden meta verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="65c2f-104">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65c2f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65c2f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65c2f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65c2f-106">Parameters</span></span>  

 `ppMemoryBuffer`  
 <span data-ttu-id="65c2f-107">dışı Birleştirilmiş derlemenin meta verilerinin boyut ve adresi hakkında bilgi içeren bir [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="65c2f-107">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65c2f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65c2f-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65c2f-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="65c2f-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65c2f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65c2f-110">Requirements</span></span>  

 <span data-ttu-id="65c2f-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65c2f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65c2f-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="65c2f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65c2f-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="65c2f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65c2f-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65c2f-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65c2f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65c2f-115">See also</span></span>

- [<span data-ttu-id="65c2f-116">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65c2f-116">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="65c2f-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="65c2f-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
