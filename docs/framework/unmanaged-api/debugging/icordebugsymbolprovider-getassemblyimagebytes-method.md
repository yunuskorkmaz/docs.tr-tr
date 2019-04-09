---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes yöntemi
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 103e724c37ae356729dd5bba3ff66c0f443f6eaa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170241"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="d886c-102">ICorDebugSymbolProvider::GetAssemblyImageBytes yöntemi</span><span class="sxs-lookup"><span data-stu-id="d886c-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="d886c-103">Birleştirilmiş derlemeye göreli sanal adres (RVA) verilen birleştirilmiş bir bütünleştirilmiş koddan verileri okur.</span><span class="sxs-lookup"><span data-stu-id="d886c-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d886c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d886c-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d886c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d886c-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="d886c-106">[in] Birleştirilmiş bir derlemeye göreli sanal adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="d886c-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="d886c-107">Birleştirilmiş derlemeden okunacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="d886c-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="d886c-108">Adresine bir işaretçi bir [Icordebugmemorybuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) bellek arabelleği ile birleştirilmiş derleme meta verileri hakkında bilgi içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="d886c-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d886c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d886c-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d886c-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d886c-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d886c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d886c-111">Requirements</span></span>  
 <span data-ttu-id="d886c-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d886c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d886c-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d886c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d886c-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d886c-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d886c-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d886c-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d886c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d886c-116">See also</span></span>

- [<span data-ttu-id="d886c-117">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d886c-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="d886c-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d886c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
