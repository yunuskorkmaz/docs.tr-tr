---
description: ': ICLRErrorReportingManager:: GetBucketParametersForCurrentException yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ba2b6cf1215e5d57f608a76a870b0a9c846ee8ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689410"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="0e36d-103">ICLRErrorReportingManager::GetBucketParametersForCurrentException Metodu</span><span class="sxs-lookup"><span data-stu-id="0e36d-103">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>

<span data-ttu-id="0e36d-104">Çağıran iş parçacığında geçerli özel durumun Watson demetini alır.</span><span class="sxs-lookup"><span data-stu-id="0e36d-104">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="0e36d-105">*Demet* , aynı kod hatası ile ilgili bir hata verileri koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="0e36d-105">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="0e36d-106">*Watson* bir özel durumla ilişkili verilerin toplanması ve çözümlenmesi için bir teknoloji kümesine başvurur.</span><span class="sxs-lookup"><span data-stu-id="0e36d-106">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e36d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e36d-107">Syntax</span></span>  
  
```cpp  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e36d-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e36d-108">Parameters</span></span>  

 `pParams`  
 <span data-ttu-id="0e36d-109">dışı Özel durum için hata verilerini içeren bir [BucketParameters](bucketparameters-structure.md) yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0e36d-109">[out] A pointer to a [BucketParameters](bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e36d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e36d-110">Requirements</span></span>  

 <span data-ttu-id="0e36d-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e36d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e36d-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0e36d-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e36d-113">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0e36d-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e36d-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e36d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e36d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e36d-115">See also</span></span>

- [<span data-ttu-id="0e36d-116">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e36d-116">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
