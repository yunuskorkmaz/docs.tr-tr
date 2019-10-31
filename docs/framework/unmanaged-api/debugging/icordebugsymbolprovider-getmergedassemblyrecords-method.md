---
title: 'ICorDebugSymbolProvider:: GetMergedAssemblyRecords yöntemi'
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: 6faf8960c06488c8fff5a076aae375529e1d0260
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138865"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="5ae9d-102">ICorDebugSymbolProvider:: GetMergedAssemblyRecords yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ae9d-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="5ae9d-103">Tüm birleştirilmiş derlemelerin sembol kayıtlarını alır.</span><span class="sxs-lookup"><span data-stu-id="5ae9d-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ae9d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ae9d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ae9d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ae9d-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="5ae9d-106">'ndaki İstenen sembol kaydı sayısı.</span><span class="sxs-lookup"><span data-stu-id="5ae9d-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="5ae9d-107">dışı Yöntemi tarafından alınan sembol kayıtlarının sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5ae9d-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="5ae9d-108">[Icordebugmergedassemblyrecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) nesnelerinin dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5ae9d-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ae9d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ae9d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ae9d-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5ae9d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ae9d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ae9d-111">Requirements</span></span>  
 <span data-ttu-id="5ae9d-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ae9d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ae9d-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5ae9d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ae9d-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5ae9d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ae9d-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ae9d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ae9d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ae9d-116">See also</span></span>

- [<span data-ttu-id="5ae9d-117">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ae9d-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="5ae9d-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5ae9d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
