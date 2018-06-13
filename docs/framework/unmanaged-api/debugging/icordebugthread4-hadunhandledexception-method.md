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
ms.openlocfilehash: 8215ddfd0f59f835d0b0dcd278b8cae9c12027d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422116"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="8cba4-102">ICorDebugThread4::HadUnhandledException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8cba4-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="8cba4-103">İş parçacığı işlenmeyen bir özel durum şimdiye kadar süredir sahip olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8cba4-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cba4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8cba4-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8cba4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8cba4-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="8cba4-106">[out] Sıralanmış numaralandırması adresini gösteren bir işaretçi [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="8cba4-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8cba4-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8cba4-107">Return Value</span></span>  
 <span data-ttu-id="8cba4-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="8cba4-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8cba4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8cba4-109">HRESULT</span></span>|<span data-ttu-id="8cba4-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8cba4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8cba4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8cba4-111">S_OK</span></span>|<span data-ttu-id="8cba4-112">İş parçacığı oluşturulmasından bu yana işlenmeyen bir özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="8cba4-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="8cba4-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8cba4-113">S_FALSE</span></span>|<span data-ttu-id="8cba4-114">İş parçacığı hiçbir zaman işlenmeyen bir özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="8cba4-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cba4-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8cba4-115">Remarks</span></span>  
 <span data-ttu-id="8cba4-116">Bu yöntem iş parçacığı işlenmeyen bir özel durum şimdiye kadar süredir sahip olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8cba4-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="8cba4-117">İşlenmeyen özel durum geri çağırma saatle tetiklenen veya yerel JIT-ekleme başlatıldığında, bu yöntem S_OK döndürmek için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8cba4-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="8cba4-118">Garantisi yoktur, [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) yöntemi işlenmeyen bir özel durum döndürür; ancak işlem henüz işlenmeyen bir özel durum geri alma sonra veya sonra devam ettirildi değil, olur Yerel JIT-ekleme.</span><span class="sxs-lookup"><span data-stu-id="8cba4-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="8cba4-119">Ayrıca, birden çok iş parçacığı işlenmeyen bir özel durum yerel JIT-ekleme tetiklenir zaman ile sağlamak için (olası rağmen) mümkündür.</span><span class="sxs-lookup"><span data-stu-id="8cba4-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="8cba4-120">Böyle bir durumda JIT-ekleme hangi özel durum tetikledi belirlemenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="8cba4-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cba4-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8cba4-121">Requirements</span></span>  
 <span data-ttu-id="8cba4-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cba4-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cba4-123">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8cba4-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8cba4-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cba4-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cba4-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cba4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cba4-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8cba4-126">See Also</span></span>  
 [<span data-ttu-id="8cba4-127">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cba4-127">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="8cba4-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8cba4-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8cba4-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8cba4-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
