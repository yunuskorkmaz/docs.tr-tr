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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1ae7cdcdc604bef98fdb8a891c9f0118edcffea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421784"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="86b1f-102">ICorDebugThread3::CreateStackWalk Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86b1f-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="86b1f-103">Oluşturur bir [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) yığını geriye doğru izleme istediğiniz iş parçacığı için nesne.</span><span class="sxs-lookup"><span data-stu-id="86b1f-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86b1f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86b1f-104">Syntax</span></span>  
  
```  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86b1f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86b1f-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="86b1f-106">[out] Bir işaretçi adresine [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) yığını geriye doğru izleme istediğiniz iş parçacığı için nesne.</span><span class="sxs-lookup"><span data-stu-id="86b1f-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86b1f-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="86b1f-107">Return Value</span></span>  
 <span data-ttu-id="86b1f-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="86b1f-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="86b1f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86b1f-109">HRESULT</span></span>|<span data-ttu-id="86b1f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86b1f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86b1f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="86b1f-111">S_OK</span></span>|<span data-ttu-id="86b1f-112">`ICorDebugStackWalk` Nesne başarıyla oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="86b1f-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="86b1f-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="86b1f-113">E_FAIL</span></span>|<span data-ttu-id="86b1f-114">`ICorDebugStackWalk` Nesne oluşturulmadı.</span><span class="sxs-lookup"><span data-stu-id="86b1f-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="86b1f-115">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="86b1f-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86b1f-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86b1f-116">Remarks</span></span>  
 <span data-ttu-id="86b1f-117">Varsa `CreateStackWalk` yöntem başarılı, döndürülen `ICorDebugStackWalk` nesnenin bağlamı iş parçacığının geçerli bağlam için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="86b1f-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86b1f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86b1f-118">Requirements</span></span>  
 <span data-ttu-id="86b1f-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86b1f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86b1f-120">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86b1f-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86b1f-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86b1f-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86b1f-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86b1f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86b1f-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86b1f-123">See Also</span></span>  
 [<span data-ttu-id="86b1f-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="86b1f-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="86b1f-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="86b1f-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
