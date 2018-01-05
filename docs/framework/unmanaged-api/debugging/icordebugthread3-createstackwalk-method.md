---
title: "ICorDebugThread3::CreateStackWalk Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread3.CreateStackWalk Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3b587a69c7acc3115c282eac065d304dc892b80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="ae035-102">ICorDebugThread3::CreateStackWalk Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae035-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="ae035-103">Oluşturur bir [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) yığını geriye doğru izleme istediğiniz iş parçacığı için nesne.</span><span class="sxs-lookup"><span data-stu-id="ae035-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae035-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae035-104">Syntax</span></span>  
  
```  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae035-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae035-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="ae035-106">[out] Bir işaretçi adresine [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) yığını geriye doğru izleme istediğiniz iş parçacığı için nesne.</span><span class="sxs-lookup"><span data-stu-id="ae035-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae035-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ae035-107">Return Value</span></span>  
 <span data-ttu-id="ae035-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="ae035-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ae035-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ae035-109">HRESULT</span></span>|<span data-ttu-id="ae035-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae035-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ae035-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ae035-111">S_OK</span></span>|<span data-ttu-id="ae035-112">`ICorDebugStackWalk` Nesne başarıyla oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="ae035-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="ae035-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ae035-113">E_FAIL</span></span>|<span data-ttu-id="ae035-114">`ICorDebugStackWalk` Nesne oluşturulmadı.</span><span class="sxs-lookup"><span data-stu-id="ae035-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="ae035-115">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="ae035-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae035-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae035-116">Remarks</span></span>  
 <span data-ttu-id="ae035-117">Varsa `CreateStackWalk` yöntem başarılı, döndürülen `ICorDebugStackWalk` nesnenin bağlamı iş parçacığının geçerli bağlam için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ae035-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae035-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae035-118">Requirements</span></span>  
 <span data-ttu-id="ae035-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae035-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae035-120">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae035-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae035-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae035-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae035-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae035-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae035-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ae035-123">See Also</span></span>  
 [<span data-ttu-id="ae035-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ae035-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ae035-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ae035-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
