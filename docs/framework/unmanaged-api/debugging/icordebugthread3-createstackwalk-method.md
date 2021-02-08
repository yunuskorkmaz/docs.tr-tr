---
description: 'Hakkında daha fazla bilgi edinin: ICorDebugThread3:: Createstackyürüme yöntemi'
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
ms.openlocfilehash: b36252160dbad14ca1bee0674b6d042072a36359
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801000"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="e1d33-103">ICorDebugThread3::CreateStackWalk Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1d33-103">ICorDebugThread3::CreateStackWalk Method</span></span>

<span data-ttu-id="e1d33-104">Yığınını aşağı doğru bırakmak istediğiniz iş parçacığı için [ıcordebugstackyürüme](icordebugstackwalk-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e1d33-104">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1d33-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1d33-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1d33-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1d33-106">Parameters</span></span>  

 `ppStackWalk`  
 <span data-ttu-id="e1d33-107">dışı Yığınını aşağı doğru bırakmak istediğiniz iş parçacığı için [ıcordebugstackyürüme](icordebugstackwalk-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e1d33-107">[out] A pointer to address of the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1d33-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e1d33-108">Return Value</span></span>  

 <span data-ttu-id="e1d33-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="e1d33-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e1d33-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1d33-110">HRESULT</span></span>|<span data-ttu-id="e1d33-111">Description</span><span class="sxs-lookup"><span data-stu-id="e1d33-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1d33-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e1d33-112">S_OK</span></span>|<span data-ttu-id="e1d33-113">`ICorDebugStackWalk`Nesne başarıyla oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="e1d33-113">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="e1d33-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e1d33-114">E_FAIL</span></span>|<span data-ttu-id="e1d33-115">`ICorDebugStackWalk`Nesne oluşturulmadı.</span><span class="sxs-lookup"><span data-stu-id="e1d33-115">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="e1d33-116">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="e1d33-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1d33-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1d33-117">Remarks</span></span>  

 <span data-ttu-id="e1d33-118">`CreateStackWalk`Yöntem başarılı olursa, döndürülen `ICorDebugStackWalk` nesnenin bağlamı iş parçacığının geçerli bağlamına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e1d33-118">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1d33-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1d33-119">Requirements</span></span>  

 <span data-ttu-id="e1d33-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1d33-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1d33-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e1d33-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1d33-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e1d33-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1d33-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1d33-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d33-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1d33-124">See also</span></span>

- [<span data-ttu-id="e1d33-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e1d33-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e1d33-126">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e1d33-126">Debugging</span></span>](index.md)
