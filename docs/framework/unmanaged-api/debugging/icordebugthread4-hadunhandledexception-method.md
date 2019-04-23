---
title: ICorDebugThread4::HadUnhandledException Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12433786f353212c1ffbd57e9bf526c3ecc60e9a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163637"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="27a3c-102">ICorDebugThread4::HadUnhandledException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="27a3c-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="27a3c-103">İş parçacığı işlenmeyen bir özel durum sahipti olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="27a3c-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27a3c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27a3c-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="27a3c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27a3c-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="27a3c-106">[out] Sıralı sabit listesi adresini bir işaretçiye [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="27a3c-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27a3c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="27a3c-107">Return Value</span></span>  
 <span data-ttu-id="27a3c-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="27a3c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="27a3c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="27a3c-109">HRESULT</span></span>|<span data-ttu-id="27a3c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27a3c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="27a3c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="27a3c-111">S_OK</span></span>|<span data-ttu-id="27a3c-112">İş parçacığı oluşturulmasından bu yana işlenmeyen bir özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="27a3c-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="27a3c-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="27a3c-113">S_FALSE</span></span>|<span data-ttu-id="27a3c-114">İş parçacığı, hiçbir zaman işlenmeyen bir özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="27a3c-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27a3c-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27a3c-115">Remarks</span></span>  
 <span data-ttu-id="27a3c-116">Bu yöntem, iş parçacığı işlenmeyen bir özel durum sahipti olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="27a3c-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="27a3c-117">İşlenmeyen özel durum geri çağırma saatle tetiklenen veya yerel JIT-ekleme başlatıldığında, bu yöntem S_OK dönmesi garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="27a3c-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="27a3c-118">Garanti yoktur, [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) yöntemi işlenmeyen bir özel durum döndürür; ancak işlem henüz işlenmemiş özel durum geri alma veya üzerine devam ettirildi değil durumunda olur Yerel JIT-ekleme.</span><span class="sxs-lookup"><span data-stu-id="27a3c-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="27a3c-119">Ayrıca, birden fazla iş parçacığı yerel JIT-ekleme tetiklenir zaman işlenmeyen bir özel durum ile sağlamak için (olasılığı karşın) mümkündür.</span><span class="sxs-lookup"><span data-stu-id="27a3c-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="27a3c-120">Böyle bir durumda, JIT-ekleme hangi özel durum harekete belirlemek için hiçbir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="27a3c-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27a3c-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27a3c-121">Requirements</span></span>  
 <span data-ttu-id="27a3c-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27a3c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27a3c-123">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27a3c-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27a3c-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27a3c-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27a3c-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27a3c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27a3c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27a3c-126">See also</span></span>

- [<span data-ttu-id="27a3c-127">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27a3c-127">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="27a3c-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="27a3c-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="27a3c-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="27a3c-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
