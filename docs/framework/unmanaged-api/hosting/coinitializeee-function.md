---
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
ms.openlocfilehash: 707e182e62f4a7b7b813e6b288c6825b0d3d2eab
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731763"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="86d3f-102">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="86d3f-102">CoInitializeEE Function</span></span>

<span data-ttu-id="86d3f-103">Ortak dil çalışma zamanı yürütme altyapısının bir işleme yüklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="86d3f-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="86d3f-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="86d3f-104">This function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="86d3f-105">Bunun yerine [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="86d3f-105">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86d3f-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="86d3f-106">Syntax</span></span>  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86d3f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86d3f-107">Parameters</span></span>  

 `fFlags`  
 <span data-ttu-id="86d3f-108">'ndaki [Coinitiee](../metadata/coinitiee-enumeration.md) sabit listesi sabitlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="86d3f-108">[in] One of the [COINITIEE](../metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86d3f-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="86d3f-109">Return Value</span></span>  

 <span data-ttu-id="86d3f-110">Bu yöntem, Winerror. h içinde tanımlanan standart COM hata kodlarını ve aşağıdaki tabloda bulunan değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="86d3f-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="86d3f-111">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="86d3f-111">Return code</span></span>|<span data-ttu-id="86d3f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86d3f-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="86d3f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="86d3f-113">S_OK</span></span>|<span data-ttu-id="86d3f-114">Yürütme altyapısı başarıyla yüklendi.</span><span class="sxs-lookup"><span data-stu-id="86d3f-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="86d3f-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="86d3f-115">S_FALSE</span></span>|<span data-ttu-id="86d3f-116">Yürütme altyapısı zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="86d3f-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="86d3f-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="86d3f-117">E_FAIL</span></span>|<span data-ttu-id="86d3f-118">Yürütme altyapısı yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="86d3f-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86d3f-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86d3f-119">Remarks</span></span>  

 <span data-ttu-id="86d3f-120">Bu yöntem, daha önce yüklenmediyse yürütme altyapısını yükler.</span><span class="sxs-lookup"><span data-stu-id="86d3f-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86d3f-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86d3f-121">Requirements</span></span>  

 <span data-ttu-id="86d3f-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86d3f-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86d3f-123">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="86d3f-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86d3f-124">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="86d3f-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="86d3f-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86d3f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d3f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86d3f-126">See also</span></span>

- [<span data-ttu-id="86d3f-127">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="86d3f-127">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
