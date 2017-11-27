---
title: "ICorDebugSymbolProvider::GetAssemblyImageBytes yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 127ebe82c32e9bf3d06c171d6cbf426d508eacaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="f8dd3-102">ICorDebugSymbolProvider::GetAssemblyImageBytes yöntemi</span><span class="sxs-lookup"><span data-stu-id="f8dd3-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="f8dd3-103">Birleştirilmiş derlemede göreli sanal adres (RVA) verilen birleştirilmiş bir bütünleştirilmiş koddan verileri okur.</span><span class="sxs-lookup"><span data-stu-id="f8dd3-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8dd3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f8dd3-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8dd3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f8dd3-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="f8dd3-106">[in] Birleştirilmiş derlemede göreli sanal adres (RAV).</span><span class="sxs-lookup"><span data-stu-id="f8dd3-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="f8dd3-107">Birleştirilmiş derlemeden okunacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="f8dd3-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="f8dd3-108">Adresine bir işaretçi bir [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) birleştirilmiş derleme meta verilerini ile bellek arabelleği hakkında bilgi içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="f8dd3-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8dd3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8dd3-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8dd3-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f8dd3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8dd3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f8dd3-111">Requirements</span></span>  
 <span data-ttu-id="f8dd3-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8dd3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8dd3-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8dd3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8dd3-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8dd3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8dd3-115">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8dd3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8dd3-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f8dd3-116">See Also</span></span>  
 [<span data-ttu-id="f8dd3-117">ICorDebugSymbolProvider arabirimi</span><span class="sxs-lookup"><span data-stu-id="f8dd3-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="f8dd3-118">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f8dd3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
