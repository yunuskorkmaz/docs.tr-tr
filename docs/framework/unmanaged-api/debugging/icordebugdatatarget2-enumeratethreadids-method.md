---
title: ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 4a65b76f384cdad68cba75af524dbe672c309624
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976492"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="c26c8-102">ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c26c8-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="c26c8-103">Etkin iş parçacığı kimliklerinin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c26c8-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c26c8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c26c8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c26c8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c26c8-105">Parameters</span></span>  
 <span data-ttu-id="c26c8-106">Cthreadıds</span><span class="sxs-lookup"><span data-stu-id="c26c8-106">cThreadIDs</span></span>  
 <span data-ttu-id="c26c8-107">'ndaki Kimlikleri döndürülebilecek en fazla iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="c26c8-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="c26c8-108">Pcthreadıds</span><span class="sxs-lookup"><span data-stu-id="c26c8-108">pcThreadIds</span></span>  
 <span data-ttu-id="c26c8-109">dışı Diziye yazılan iş parçacığı `ULONG32` kimliklerinin gerçek sayısını gösteren bir işaretçisi. `pThreadIds`</span><span class="sxs-lookup"><span data-stu-id="c26c8-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="c26c8-110">Pthreadıds</span><span class="sxs-lookup"><span data-stu-id="c26c8-110">pThreadIDs</span></span>  
 <span data-ttu-id="c26c8-111">Bir dizi iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c26c8-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c26c8-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c26c8-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c26c8-113">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c26c8-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c26c8-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c26c8-114">Requirements</span></span>  
 <span data-ttu-id="c26c8-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md). **Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c26c8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c26c8-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c26c8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c26c8-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c26c8-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c26c8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c26c8-118">See also</span></span>

- [<span data-ttu-id="c26c8-119">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c26c8-119">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="c26c8-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c26c8-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
