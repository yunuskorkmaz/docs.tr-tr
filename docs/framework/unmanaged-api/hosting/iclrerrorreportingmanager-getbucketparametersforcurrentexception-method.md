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
ms.openlocfilehash: 969d74933e908674225684a2e77d5c4804b86122
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615650"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="e9bc8-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Metodu</span><span class="sxs-lookup"><span data-stu-id="e9bc8-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="e9bc8-103">Çağıran iş parçacığında geçerli özel durumun Watson demetini alır.</span><span class="sxs-lookup"><span data-stu-id="e9bc8-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="e9bc8-104">*Demet* , aynı kod hatası ile ilgili bir hata verileri koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="e9bc8-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="e9bc8-105">*Watson* bir özel durumla ilişkili verilerin toplanması ve çözümlenmesi için bir teknoloji kümesine başvurur.</span><span class="sxs-lookup"><span data-stu-id="e9bc8-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9bc8-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e9bc8-106">Syntax</span></span>  
  
```cpp  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9bc8-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9bc8-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="e9bc8-108">dışı Özel durum için hata verilerini içeren bir [BucketParameters](bucketparameters-structure.md) yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e9bc8-108">[out] A pointer to a [BucketParameters](bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9bc8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9bc8-109">Requirements</span></span>  
 <span data-ttu-id="e9bc8-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9bc8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9bc8-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e9bc8-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9bc8-112">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="e9bc8-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9bc8-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9bc8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9bc8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9bc8-114">See also</span></span>

- [<span data-ttu-id="e9bc8-115">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9bc8-115">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
