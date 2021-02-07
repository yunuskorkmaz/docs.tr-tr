---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugDataTarget2:: EnumerateThreadIDs yöntemi'
title: ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 5bbda67e6c6de81e9de566a68f772f324d79b92f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710562"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="acadf-103">ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="acadf-103">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>

<span data-ttu-id="acadf-104">Etkin iş parçacığı kimliklerinin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="acadf-104">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acadf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="acadf-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acadf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="acadf-106">Parameters</span></span>  

 <span data-ttu-id="acadf-107">Cthreadıds</span><span class="sxs-lookup"><span data-stu-id="acadf-107">cThreadIDs</span></span>  
 <span data-ttu-id="acadf-108">'ndaki Kimlikleri döndürülebilecek en fazla iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="acadf-108">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="acadf-109">Pcthreadıds</span><span class="sxs-lookup"><span data-stu-id="acadf-109">pcThreadIds</span></span>  
 <span data-ttu-id="acadf-110">dışı `ULONG32` Diziye yazılan iş parçacığı kimliklerinin gerçek sayısını gösteren bir işaretçisi `pThreadIds` .</span><span class="sxs-lookup"><span data-stu-id="acadf-110">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="acadf-111">Pthreadıds</span><span class="sxs-lookup"><span data-stu-id="acadf-111">pThreadIDs</span></span>  
 <span data-ttu-id="acadf-112">Bir dizi iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="acadf-112">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acadf-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="acadf-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acadf-114">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="acadf-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acadf-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="acadf-115">Requirements</span></span>  

 <span data-ttu-id="acadf-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md). **Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="acadf-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acadf-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="acadf-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acadf-118">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acadf-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acadf-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acadf-119">See also</span></span>

- [<span data-ttu-id="acadf-120">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="acadf-120">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="acadf-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="acadf-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
