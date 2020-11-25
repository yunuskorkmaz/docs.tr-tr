---
title: 'ICorDebugSymbolProvider:: Getassemblyımagebytes yöntemi'
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: b52614065d599edf8e556524c33e8bc50b4924ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709186"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="0b09b-102">ICorDebugSymbolProvider:: Getassemblyımagebytes yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b09b-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>

<span data-ttu-id="0b09b-103">Birleştirilen derlemede göreli bir sanal adres (RVA) verilen birleştirilmiş bir derlemeden verileri okur.</span><span class="sxs-lookup"><span data-stu-id="0b09b-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b09b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0b09b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b09b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b09b-105">Parameters</span></span>  

 `rva`  
 <span data-ttu-id="0b09b-106">'ndaki Birleştirilmiş bir derlemede göreli bir sanal adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="0b09b-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="0b09b-107">Birleştirilmiş derlemeden okunacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="0b09b-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="0b09b-108">Birleştirilmiş bütünleştirilmiş kod meta verileri ile bellek arabelleği hakkında bilgi içeren bir [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0b09b-108">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b09b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b09b-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b09b-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0b09b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b09b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b09b-111">Requirements</span></span>  

 <span data-ttu-id="0b09b-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b09b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b09b-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0b09b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b09b-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0b09b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b09b-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b09b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b09b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b09b-116">See also</span></span>

- [<span data-ttu-id="0b09b-117">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b09b-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="0b09b-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0b09b-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
