---
title: ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1dc5f8b7fa308bdb0fb270c11e044244839a7b47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910295"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="5d941-102">ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d941-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="5d941-103">Etkin iş parçacığı kimliklerinin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d941-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d941-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d941-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d941-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d941-105">Parameters</span></span>  
 <span data-ttu-id="5d941-106">Cthreadıds</span><span class="sxs-lookup"><span data-stu-id="5d941-106">cThreadIDs</span></span>  
 <span data-ttu-id="5d941-107">'ndaki Kimlikleri döndürülebilecek en fazla iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="5d941-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="5d941-108">Pcthreadıds</span><span class="sxs-lookup"><span data-stu-id="5d941-108">pcThreadIds</span></span>  
 <span data-ttu-id="5d941-109">dışı Diziye`pThreadIds` yazılan iş parçacığı `ULONG32` kimliklerinin gerçek sayısını gösteren bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5d941-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="5d941-110">Pthreadıds</span><span class="sxs-lookup"><span data-stu-id="5d941-110">pThreadIDs</span></span>  
 <span data-ttu-id="5d941-111">Bir dizi iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="5d941-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d941-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d941-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d941-113">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d941-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d941-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d941-114">Requirements</span></span>  
 <span data-ttu-id="5d941-115">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md). **Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5d941-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d941-116">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5d941-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d941-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d941-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d941-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d941-118">See also</span></span>

- [<span data-ttu-id="5d941-119">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d941-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="5d941-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5d941-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
