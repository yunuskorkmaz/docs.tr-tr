---
description: ': ICorDebugSymbolProvider:: Getassemblyımagebytes yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugSymbolProvider:: Getassemblyımagebytes yöntemi'
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: 2e08b23e35913e8767135d75d28ff66efc890565
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717283"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="82e96-103">ICorDebugSymbolProvider:: Getassemblyımagebytes yöntemi</span><span class="sxs-lookup"><span data-stu-id="82e96-103">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>

<span data-ttu-id="82e96-104">Birleştirilen derlemede göreli bir sanal adres (RVA) verilen birleştirilmiş bir derlemeden verileri okur.</span><span class="sxs-lookup"><span data-stu-id="82e96-104">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82e96-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82e96-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82e96-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82e96-106">Parameters</span></span>  

 `rva`  
 <span data-ttu-id="82e96-107">'ndaki Birleştirilmiş bir derlemede göreli bir sanal adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="82e96-107">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="82e96-108">Birleştirilmiş derlemeden okunacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="82e96-108">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="82e96-109">Birleştirilmiş bütünleştirilmiş kod meta verileri ile bellek arabelleği hakkında bilgi içeren bir [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="82e96-109">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82e96-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82e96-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82e96-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="82e96-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82e96-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82e96-112">Requirements</span></span>  

 <span data-ttu-id="82e96-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82e96-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82e96-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="82e96-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82e96-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="82e96-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82e96-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82e96-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e96-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82e96-117">See also</span></span>

- [<span data-ttu-id="82e96-118">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82e96-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="82e96-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="82e96-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
