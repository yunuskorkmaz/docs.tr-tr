---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes Yöntemi
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: 6361b12802876ef480acbe1cc13f32b77ba0be49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178486"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="7651f-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7651f-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="7651f-103">Birleştirilmiş derlemede göreceli sanal adres (RVA) verilen birleştirilmiş bir derlemedeki verileri okur.</span><span class="sxs-lookup"><span data-stu-id="7651f-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7651f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7651f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7651f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7651f-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="7651f-106">[içinde] Birleştirilmiş bir derlemede göreceli sanal adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="7651f-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="7651f-107">Birleştirilmiş derlemeden okunacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="7651f-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="7651f-108">Birleştirilmiş derleme meta verileriyle bellek arabelleği hakkında bilgi içeren bir [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) nesnesinin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7651f-108">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7651f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7651f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7651f-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7651f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7651f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7651f-111">Requirements</span></span>  
 <span data-ttu-id="7651f-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7651f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7651f-113">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7651f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7651f-114">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7651f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7651f-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7651f-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7651f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7651f-116">See also</span></span>

- [<span data-ttu-id="7651f-117">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7651f-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="7651f-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7651f-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
