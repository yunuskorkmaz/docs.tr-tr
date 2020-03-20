---
title: ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 120a970aac33b1ab06ae47335a959d2791f893ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178989"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="751a0-102">ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="751a0-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="751a0-103">Etkin iş parçacığı işleri işleri işleri için bir liste verir.</span><span class="sxs-lookup"><span data-stu-id="751a0-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="751a0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="751a0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="751a0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="751a0-105">Parameters</span></span>  
 <span data-ttu-id="751a0-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="751a0-106">cThreadIDs</span></span>  
 <span data-ttu-id="751a0-107">[içinde] Kimlikleri döndürülebilen maksimum iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="751a0-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="751a0-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="751a0-108">pcThreadIds</span></span>  
 <span data-ttu-id="751a0-109">[çıkış] Diziye yazılmış `ULONG32` gerçek iş parçacığı dislerini gösteren bir işaretçi. `pThreadIds`</span><span class="sxs-lookup"><span data-stu-id="751a0-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="751a0-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="751a0-110">pThreadIDs</span></span>  
 <span data-ttu-id="751a0-111">Bir dizi iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="751a0-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="751a0-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="751a0-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="751a0-113">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="751a0-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="751a0-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="751a0-114">Requirements</span></span>  
 <span data-ttu-id="751a0-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md). **Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="751a0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="751a0-116">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="751a0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="751a0-117">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="751a0-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="751a0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="751a0-118">See also</span></span>

- [<span data-ttu-id="751a0-119">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="751a0-119">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="751a0-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="751a0-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
