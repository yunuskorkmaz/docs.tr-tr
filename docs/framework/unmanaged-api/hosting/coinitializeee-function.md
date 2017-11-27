---
title: "CoInitializeEE İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoInitializeEE
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CoInitializeEE
helpviewer_keywords: CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 429d055ec0853d04f794b063a76a395d98aceb4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="coinitializeee-function"></a><span data-ttu-id="cabd1-102">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="cabd1-102">CoInitializeEE Function</span></span>
<span data-ttu-id="cabd1-103">Ortak dil çalışma zamanı yürütme altyapısı bir işlemine yüklendi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cabd1-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="cabd1-104">Bu işlev de kullanım dışı [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cabd1-104">This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="cabd1-105">Kullanım [Iclrruntimehost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="cabd1-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cabd1-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cabd1-106">Syntax</span></span>  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cabd1-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cabd1-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="cabd1-108">[in] Aşağıdakilerden birini [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) numaralandırma sabitleri.</span><span class="sxs-lookup"><span data-stu-id="cabd1-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cabd1-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cabd1-109">Return Value</span></span>  
 <span data-ttu-id="cabd1-110">Bu yöntem, Winerror.h'de ve değerleri aşağıdaki tabloda tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="cabd1-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="cabd1-111">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="cabd1-111">Return code</span></span>|<span data-ttu-id="cabd1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cabd1-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="cabd1-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="cabd1-113">S_OK</span></span>|<span data-ttu-id="cabd1-114">Yürütme altyapısı başarıyla yüklendi.</span><span class="sxs-lookup"><span data-stu-id="cabd1-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="cabd1-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="cabd1-115">S_FALSE</span></span>|<span data-ttu-id="cabd1-116">Yürütme altyapısı zaten yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="cabd1-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="cabd1-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cabd1-117">E_FAIL</span></span>|<span data-ttu-id="cabd1-118">Yürütme alt yapısı yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="cabd1-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cabd1-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cabd1-119">Remarks</span></span>  
 <span data-ttu-id="cabd1-120">Daha önce yüklü değilse bu yöntem yürütme altyapısı yükler.</span><span class="sxs-lookup"><span data-stu-id="cabd1-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cabd1-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cabd1-121">Requirements</span></span>  
 <span data-ttu-id="cabd1-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cabd1-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cabd1-123">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cabd1-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cabd1-124">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cabd1-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cabd1-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cabd1-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cabd1-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cabd1-126">See Also</span></span>  
 [<span data-ttu-id="cabd1-127">Meta veri genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="cabd1-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
