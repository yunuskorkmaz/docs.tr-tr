---
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords yöntemi
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a979fd3dd8fc8fc4266f7bd69be0e71b8a400a6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477685"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="5290a-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords yöntemi</span><span class="sxs-lookup"><span data-stu-id="5290a-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="5290a-103">Birleştirilmiş tüm derlemeler için Sembol kayıtları alır.</span><span class="sxs-lookup"><span data-stu-id="5290a-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5290a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5290a-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5290a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5290a-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="5290a-106">[in] İstenen sembol kayıt sayısı.</span><span class="sxs-lookup"><span data-stu-id="5290a-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="5290a-107">[out] Yöntemi tarafından alınan sembol kayıt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5290a-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="5290a-108">Bir dizi işaretçi [Icordebugmergedassemblyrecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5290a-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5290a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5290a-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5290a-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5290a-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5290a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5290a-111">Requirements</span></span>  
 <span data-ttu-id="5290a-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5290a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5290a-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5290a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5290a-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5290a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5290a-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5290a-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5290a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5290a-116">See also</span></span>
- [<span data-ttu-id="5290a-117">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5290a-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="5290a-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5290a-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
