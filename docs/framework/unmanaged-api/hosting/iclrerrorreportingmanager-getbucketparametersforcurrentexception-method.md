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
ms.openlocfilehash: b24f8ed4f5e2c6e0022f5599f2ab8c44a30a561a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129273"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="17684-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Metodu</span><span class="sxs-lookup"><span data-stu-id="17684-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="17684-103">Çağıran iş parçacığında geçerli özel durumun Watson demetini alır.</span><span class="sxs-lookup"><span data-stu-id="17684-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="17684-104">*Demet* , aynı kod hatası ile ilgili bir hata verileri koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="17684-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="17684-105">*Watson* bir özel durumla ilişkili verilerin toplanması ve çözümlenmesi için bir teknoloji kümesine başvurur.</span><span class="sxs-lookup"><span data-stu-id="17684-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17684-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17684-106">Syntax</span></span>  
  
```cpp  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17684-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17684-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="17684-108">dışı Özel durum için hata verilerini içeren bir [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="17684-108">[out] A pointer to a [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17684-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17684-109">Requirements</span></span>  
 <span data-ttu-id="17684-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17684-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17684-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="17684-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17684-112">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="17684-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17684-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17684-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17684-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17684-114">See also</span></span>

- [<span data-ttu-id="17684-115">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17684-115">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
