---
title: "ICorDebugSymbolProvider::GetMergedAssemblyRecords yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f7515479ae5fbe490496bac79f102b02700dcee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="ff025-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff025-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="ff025-103">Sembol kayıtları için tüm birleştirilmiş derlemeleri alır.</span><span class="sxs-lookup"><span data-stu-id="ff025-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff025-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff025-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff025-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff025-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="ff025-106">[in] İstenen sembol kayıt sayısı.</span><span class="sxs-lookup"><span data-stu-id="ff025-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="ff025-107">[out] Yöntemi tarafından alınan sembol kayıt sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ff025-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="ff025-108">Bir dizi için bir işaretçi [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ff025-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff025-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff025-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff025-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff025-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff025-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff025-111">Requirements</span></span>  
 <span data-ttu-id="ff025-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff025-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff025-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff025-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff025-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff025-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff025-115">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff025-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff025-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ff025-116">See Also</span></span>  
 [<span data-ttu-id="ff025-117">ICorDebugSymbolProvider arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff025-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="ff025-118">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ff025-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
