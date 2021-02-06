---
description: ': ICorDebugSymbolProvider:: GetMergedAssemblyRecords yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugSymbolProvider:: GetMergedAssemblyRecords yöntemi'
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: f12bb3a49d7b49f9f8916c9d04417340502d44ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659887"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="43fda-103">ICorDebugSymbolProvider:: GetMergedAssemblyRecords yöntemi</span><span class="sxs-lookup"><span data-stu-id="43fda-103">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>

<span data-ttu-id="43fda-104">Tüm birleştirilmiş derlemelerin sembol kayıtlarını alır.</span><span class="sxs-lookup"><span data-stu-id="43fda-104">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43fda-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43fda-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43fda-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43fda-106">Parameters</span></span>  

 `cRequestedRecords`  
 <span data-ttu-id="43fda-107">'ndaki İstenen sembol kaydı sayısı.</span><span class="sxs-lookup"><span data-stu-id="43fda-107">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="43fda-108">dışı Yöntemi tarafından alınan sembol kayıtlarının sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="43fda-108">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="43fda-109">[Icordebugmergedassemblyrecord](icordebugmergedassemblyrecord-interface.md) nesnelerinin dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="43fda-109">A pointer to an array of [ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43fda-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43fda-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43fda-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="43fda-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43fda-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43fda-112">Requirements</span></span>  

 <span data-ttu-id="43fda-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43fda-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43fda-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="43fda-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43fda-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="43fda-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43fda-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43fda-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43fda-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43fda-117">See also</span></span>

- [<span data-ttu-id="43fda-118">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43fda-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="43fda-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="43fda-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
