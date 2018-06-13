---
title: CoInitializeEE İşlevi
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bbd25909e70826f8cd29076c1eb62a4da6779cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435407"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="73212-102">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="73212-102">CoInitializeEE Function</span></span>
<span data-ttu-id="73212-103">Ortak dil çalışma zamanı yürütme altyapısı bir işlemine yüklendi sağlar.</span><span class="sxs-lookup"><span data-stu-id="73212-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="73212-104">Bu işlev de kullanım dışı [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73212-104">This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="73212-105">Kullanım [Iclrruntimehost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="73212-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73212-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73212-106">Syntax</span></span>  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73212-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73212-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="73212-108">[in] Aşağıdakilerden birini [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) numaralandırma sabitleri.</span><span class="sxs-lookup"><span data-stu-id="73212-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73212-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="73212-109">Return Value</span></span>  
 <span data-ttu-id="73212-110">Bu yöntem, Winerror.h'de ve değerleri aşağıdaki tabloda tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="73212-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="73212-111">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="73212-111">Return code</span></span>|<span data-ttu-id="73212-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73212-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="73212-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="73212-113">S_OK</span></span>|<span data-ttu-id="73212-114">Yürütme altyapısı başarıyla yüklendi.</span><span class="sxs-lookup"><span data-stu-id="73212-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="73212-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="73212-115">S_FALSE</span></span>|<span data-ttu-id="73212-116">Yürütme altyapısı zaten yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="73212-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="73212-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="73212-117">E_FAIL</span></span>|<span data-ttu-id="73212-118">Yürütme alt yapısı yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="73212-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73212-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73212-119">Remarks</span></span>  
 <span data-ttu-id="73212-120">Daha önce yüklü değilse bu yöntem yürütme altyapısı yükler.</span><span class="sxs-lookup"><span data-stu-id="73212-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73212-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73212-121">Requirements</span></span>  
 <span data-ttu-id="73212-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73212-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73212-123">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="73212-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="73212-124">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="73212-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="73212-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73212-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73212-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73212-126">See Also</span></span>  
 [<span data-ttu-id="73212-127">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="73212-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
