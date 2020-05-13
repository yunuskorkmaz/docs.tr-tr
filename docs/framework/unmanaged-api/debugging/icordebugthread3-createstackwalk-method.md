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
ms.openlocfilehash: f2850e6c9cbb2250a08ab4a0e34c69e377d3a23d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375850"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="bec1a-102">ICorDebugThread3::CreateStackWalk Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bec1a-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="bec1a-103">Yığınını aşağı doğru bırakmak istediğiniz iş parçacığı için [ıcordebugstackyürüme](icordebugstackwalk-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bec1a-103">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bec1a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bec1a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bec1a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bec1a-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="bec1a-106">dışı Yığınını aşağı doğru bırakmak istediğiniz iş parçacığı için [ıcordebugstackyürüme](icordebugstackwalk-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bec1a-106">[out] A pointer to address of the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bec1a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bec1a-107">Return Value</span></span>  
 <span data-ttu-id="bec1a-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="bec1a-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bec1a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bec1a-109">HRESULT</span></span>|<span data-ttu-id="bec1a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bec1a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bec1a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bec1a-111">S_OK</span></span>|<span data-ttu-id="bec1a-112">`ICorDebugStackWalk`Nesne başarıyla oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="bec1a-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="bec1a-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bec1a-113">E_FAIL</span></span>|<span data-ttu-id="bec1a-114">`ICorDebugStackWalk`Nesne oluşturulmadı.</span><span class="sxs-lookup"><span data-stu-id="bec1a-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="bec1a-115">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="bec1a-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bec1a-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bec1a-116">Remarks</span></span>  
 <span data-ttu-id="bec1a-117">`CreateStackWalk`Yöntem başarılı olursa, döndürülen `ICorDebugStackWalk` nesnenin bağlamı iş parçacığının geçerli bağlamına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bec1a-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bec1a-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bec1a-118">Requirements</span></span>  
 <span data-ttu-id="bec1a-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bec1a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bec1a-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bec1a-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bec1a-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bec1a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bec1a-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bec1a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec1a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bec1a-123">See also</span></span>

- [<span data-ttu-id="bec1a-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bec1a-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="bec1a-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="bec1a-125">Debugging</span></span>](index.md)
