---
title: ICorDebugThread3::CreateStackWalk Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.CreateStackWalk Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type:
- apiref
ms.openlocfilehash: fb9d07fffd2ec98225ce60b211f525f8dafd9725
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691076"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="ffca7-102">ICorDebugThread3::CreateStackWalk Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ffca7-102">ICorDebugThread3::CreateStackWalk Method</span></span>

<span data-ttu-id="ffca7-103">Yığınını aşağı doğru bırakmak istediğiniz iş parçacığı için [ıcordebugstackyürüme](icordebugstackwalk-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ffca7-103">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffca7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ffca7-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffca7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ffca7-105">Parameters</span></span>  

 `ppStackWalk`  
 <span data-ttu-id="ffca7-106">dışı Yığınını aşağı doğru bırakmak istediğiniz iş parçacığı için [ıcordebugstackyürüme](icordebugstackwalk-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ffca7-106">[out] A pointer to address of the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffca7-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ffca7-107">Return Value</span></span>  

 <span data-ttu-id="ffca7-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="ffca7-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ffca7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ffca7-109">HRESULT</span></span>|<span data-ttu-id="ffca7-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ffca7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ffca7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ffca7-111">S_OK</span></span>|<span data-ttu-id="ffca7-112">`ICorDebugStackWalk`Nesne başarıyla oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="ffca7-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="ffca7-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ffca7-113">E_FAIL</span></span>|<span data-ttu-id="ffca7-114">`ICorDebugStackWalk`Nesne oluşturulmadı.</span><span class="sxs-lookup"><span data-stu-id="ffca7-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="ffca7-115">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="ffca7-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffca7-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ffca7-116">Remarks</span></span>  

 <span data-ttu-id="ffca7-117">`CreateStackWalk`Yöntem başarılı olursa, döndürülen `ICorDebugStackWalk` nesnenin bağlamı iş parçacığının geçerli bağlamına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ffca7-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffca7-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ffca7-118">Requirements</span></span>  

 <span data-ttu-id="ffca7-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffca7-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffca7-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ffca7-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffca7-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ffca7-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffca7-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffca7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffca7-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffca7-123">See also</span></span>

- [<span data-ttu-id="ffca7-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ffca7-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ffca7-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ffca7-125">Debugging</span></span>](index.md)
