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
ms.openlocfilehash: 7969d8482970b13951938203262f6ce8f9bf574a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229309"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="29b12-102">ICorDebugThread3::CreateStackWalk Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29b12-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="29b12-103">Oluşturur bir [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) yığın geriye doğru izleme istediğiniz iş parçacığı için nesne.</span><span class="sxs-lookup"><span data-stu-id="29b12-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29b12-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29b12-104">Syntax</span></span>  
  
```  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29b12-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29b12-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="29b12-106">[out] Adresini bir işaretçiye [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) yığın geriye doğru izleme istediğiniz iş parçacığı için nesne.</span><span class="sxs-lookup"><span data-stu-id="29b12-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29b12-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="29b12-107">Return Value</span></span>  
 <span data-ttu-id="29b12-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="29b12-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="29b12-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29b12-109">HRESULT</span></span>|<span data-ttu-id="29b12-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29b12-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="29b12-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="29b12-111">S_OK</span></span>|<span data-ttu-id="29b12-112">`ICorDebugStackWalk` Nesne başarıyla oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="29b12-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="29b12-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="29b12-113">E_FAIL</span></span>|<span data-ttu-id="29b12-114">`ICorDebugStackWalk` Nesnesi oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="29b12-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="29b12-115">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="29b12-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29b12-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29b12-116">Remarks</span></span>  
 <span data-ttu-id="29b12-117">Varsa `CreateStackWalk` yöntem başarılı, döndürülen `ICorDebugStackWalk` nesnenin bağlamı, iş parçacığının geçerli bağlam için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="29b12-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29b12-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29b12-118">Requirements</span></span>  
 <span data-ttu-id="29b12-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29b12-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29b12-120">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29b12-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29b12-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29b12-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29b12-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29b12-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29b12-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29b12-123">See also</span></span>

- [<span data-ttu-id="29b12-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="29b12-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="29b12-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="29b12-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
