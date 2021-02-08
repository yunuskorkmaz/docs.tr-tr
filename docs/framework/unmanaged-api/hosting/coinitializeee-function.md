---
description: 'Daha fazla bilgi edinin: Coınitialeee Işlevi'
title: CoInitializeEE İşlevi
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
ms.openlocfilehash: 9664324c569ed4de73262491cf8eda8296b3c3a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799830"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="9c390-103">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="9c390-103">CoInitializeEE Function</span></span>

<span data-ttu-id="9c390-104">Ortak dil çalışma zamanı yürütme altyapısının bir işleme yüklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c390-104">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="9c390-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="9c390-105">This function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="9c390-106">Bunun yerine [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9c390-106">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c390-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c390-107">Syntax</span></span>  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c390-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c390-108">Parameters</span></span>  

 `fFlags`  
 <span data-ttu-id="9c390-109">'ndaki [Coinitiee](../metadata/coinitiee-enumeration.md) sabit listesi sabitlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="9c390-109">[in] One of the [COINITIEE](../metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c390-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9c390-110">Return Value</span></span>  

 <span data-ttu-id="9c390-111">Bu yöntem, Winerror. h içinde tanımlanan standart COM hata kodlarını ve aşağıdaki tabloda bulunan değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="9c390-111">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="9c390-112">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="9c390-112">Return code</span></span>|<span data-ttu-id="9c390-113">Description</span><span class="sxs-lookup"><span data-stu-id="9c390-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="9c390-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c390-114">S_OK</span></span>|<span data-ttu-id="9c390-115">Yürütme altyapısı başarıyla yüklendi.</span><span class="sxs-lookup"><span data-stu-id="9c390-115">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="9c390-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9c390-116">S_FALSE</span></span>|<span data-ttu-id="9c390-117">Yürütme altyapısı zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="9c390-117">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="9c390-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9c390-118">E_FAIL</span></span>|<span data-ttu-id="9c390-119">Yürütme altyapısı yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="9c390-119">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c390-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c390-120">Remarks</span></span>  

 <span data-ttu-id="9c390-121">Bu yöntem, daha önce yüklenmediyse yürütme altyapısını yükler.</span><span class="sxs-lookup"><span data-stu-id="9c390-121">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c390-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c390-122">Requirements</span></span>  

 <span data-ttu-id="9c390-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c390-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c390-124">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9c390-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c390-125">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9c390-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c390-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c390-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c390-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c390-127">See also</span></span>

- [<span data-ttu-id="9c390-128">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9c390-128">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
