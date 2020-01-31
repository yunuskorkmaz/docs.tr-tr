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
ms.openlocfilehash: 64f6bc9abb8105cdfa942c2aaca71994e8a91765
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791411"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="c1c58-102">ICorDebugThread3::CreateStackWalk Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1c58-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="c1c58-103">Yığınını aşağı doğru bırakmak istediğiniz iş parçacığı için [ıcordebugstackyürüme](icordebugstackwalk-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c1c58-103">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1c58-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1c58-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1c58-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1c58-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="c1c58-106">dışı Yığınını aşağı doğru bırakmak istediğiniz iş parçacığı için [ıcordebugstackyürüme](icordebugstackwalk-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c1c58-106">[out] A pointer to address of the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1c58-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c1c58-107">Return Value</span></span>  
 <span data-ttu-id="c1c58-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="c1c58-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c1c58-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1c58-109">HRESULT</span></span>|<span data-ttu-id="c1c58-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1c58-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1c58-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1c58-111">S_OK</span></span>|<span data-ttu-id="c1c58-112">`ICorDebugStackWalk` nesnesi başarıyla oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="c1c58-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="c1c58-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c1c58-113">E_FAIL</span></span>|<span data-ttu-id="c1c58-114">`ICorDebugStackWalk` nesnesi oluşturulmamış.</span><span class="sxs-lookup"><span data-stu-id="c1c58-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="c1c58-115">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="c1c58-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1c58-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1c58-116">Remarks</span></span>  
 <span data-ttu-id="c1c58-117">`CreateStackWalk` yöntemi başarılı olursa, döndürülen `ICorDebugStackWalk` nesnesinin bağlamı iş parçacığının geçerli bağlamına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c1c58-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1c58-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1c58-118">Requirements</span></span>  
 <span data-ttu-id="c1c58-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1c58-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1c58-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c1c58-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1c58-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c1c58-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1c58-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1c58-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1c58-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1c58-123">See also</span></span>

- [<span data-ttu-id="c1c58-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c1c58-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c1c58-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c1c58-125">Debugging</span></span>](index.md)
