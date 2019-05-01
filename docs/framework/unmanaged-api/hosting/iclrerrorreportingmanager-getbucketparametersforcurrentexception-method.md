---
title: ICLRErrorReportingManager::GetBucketParametersForCurrentException Metodu
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.GetBucketParametersForCurrentException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException
helpviewer_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException method [.NET Framework hosting]
- GetBucketParametersForCurrentException method [.NET Framework hosting]
ms.assetid: a13ec8a6-8e18-4acb-8054-77f5b1a0e0b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cb2a8d2a4e089d16b6c2129c165a9d8b6828f3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969839"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="d4324-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Metodu</span><span class="sxs-lookup"><span data-stu-id="d4324-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="d4324-103">Watson demet çağıran iş parçacığında geçerli özel durumu alır.</span><span class="sxs-lookup"><span data-stu-id="d4324-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="d4324-104">A *demet* aynı kod hatası için ilgili veriler hata oluşan bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="d4324-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="d4324-105">*Watson* bir özel durumla ilişkili verileri toplayıp analiz eden için teknoloji kümesi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="d4324-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4324-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4324-106">Syntax</span></span>  
  
```  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4324-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4324-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="d4324-108">[out] Bir işaretçi bir [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) içeren özel durum için hata veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="d4324-108">[out] A pointer to a [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4324-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4324-109">Requirements</span></span>  
 <span data-ttu-id="d4324-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4324-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4324-111">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d4324-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4324-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d4324-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4324-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4324-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4324-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4324-114">See also</span></span>

- [<span data-ttu-id="d4324-115">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4324-115">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
