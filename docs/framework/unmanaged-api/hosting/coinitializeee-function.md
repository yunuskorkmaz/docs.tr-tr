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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18f1a4ede1a362860df1271835600e7b867eac00
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127770"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="a0ad8-102">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="a0ad8-102">CoInitializeEE Function</span></span>
<span data-ttu-id="a0ad8-103">Ortak dil çalışma zamanı yürütme altyapısının bir işleme yüklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0ad8-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="a0ad8-104">Bu işlev kullanım dışı [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0ad8-104">This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="a0ad8-105">Kullanım [Iclrruntimehost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="a0ad8-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0ad8-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0ad8-106">Syntax</span></span>  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0ad8-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a0ad8-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="a0ad8-108">[in] Aşağıdakilerden birini [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) numaralandırma sabitlerini.</span><span class="sxs-lookup"><span data-stu-id="a0ad8-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0ad8-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a0ad8-109">Return Value</span></span>  
 <span data-ttu-id="a0ad8-110">Bu yöntem, wınerror ve değerleri aşağıdaki tabloda tanımlandığı gibi standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="a0ad8-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="a0ad8-111">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="a0ad8-111">Return code</span></span>|<span data-ttu-id="a0ad8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0ad8-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a0ad8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0ad8-113">S_OK</span></span>|<span data-ttu-id="a0ad8-114">Yürütme altyapısı başarıyla yüklendi.</span><span class="sxs-lookup"><span data-stu-id="a0ad8-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="a0ad8-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a0ad8-115">S_FALSE</span></span>|<span data-ttu-id="a0ad8-116">Yürütme altyapısı zaten yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="a0ad8-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="a0ad8-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a0ad8-117">E_FAIL</span></span>|<span data-ttu-id="a0ad8-118">Yürütme altyapısı yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="a0ad8-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0ad8-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0ad8-119">Remarks</span></span>  
 <span data-ttu-id="a0ad8-120">Önceden yüklü değilse bu yöntem yürütme altyapısı yükler.</span><span class="sxs-lookup"><span data-stu-id="a0ad8-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0ad8-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0ad8-121">Requirements</span></span>  
 <span data-ttu-id="a0ad8-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0ad8-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0ad8-123">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a0ad8-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0ad8-124">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a0ad8-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a0ad8-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0ad8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0ad8-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0ad8-126">See also</span></span>

- [<span data-ttu-id="a0ad8-127">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a0ad8-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
