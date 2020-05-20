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
ms.openlocfilehash: 57508a2df3a49c39d25347f2a3038442c37278da
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616768"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="c1cdc-102">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="c1cdc-102">CoInitializeEE Function</span></span>
<span data-ttu-id="c1cdc-103">Ortak dil çalışma zamanı yürütme altyapısının bir işleme yüklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1cdc-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="c1cdc-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="c1cdc-104">This function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="c1cdc-105">Bunun yerine [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1cdc-105">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1cdc-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c1cdc-106">Syntax</span></span>  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1cdc-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1cdc-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="c1cdc-108">'ndaki [Coinitiee](../metadata/coinitiee-enumeration.md) sabit listesi sabitlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="c1cdc-108">[in] One of the [COINITIEE](../metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1cdc-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c1cdc-109">Return Value</span></span>  
 <span data-ttu-id="c1cdc-110">Bu yöntem, Winerror. h içinde tanımlanan standart COM hata kodlarını ve aşağıdaki tabloda bulunan değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c1cdc-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="c1cdc-111">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="c1cdc-111">Return code</span></span>|<span data-ttu-id="c1cdc-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1cdc-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c1cdc-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1cdc-113">S_OK</span></span>|<span data-ttu-id="c1cdc-114">Yürütme altyapısı başarıyla yüklendi.</span><span class="sxs-lookup"><span data-stu-id="c1cdc-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="c1cdc-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c1cdc-115">S_FALSE</span></span>|<span data-ttu-id="c1cdc-116">Yürütme altyapısı zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="c1cdc-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="c1cdc-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c1cdc-117">E_FAIL</span></span>|<span data-ttu-id="c1cdc-118">Yürütme altyapısı yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="c1cdc-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1cdc-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1cdc-119">Remarks</span></span>  
 <span data-ttu-id="c1cdc-120">Bu yöntem, daha önce yüklenmediyse yürütme altyapısını yükler.</span><span class="sxs-lookup"><span data-stu-id="c1cdc-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1cdc-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1cdc-121">Requirements</span></span>  
 <span data-ttu-id="c1cdc-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1cdc-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1cdc-123">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c1cdc-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1cdc-124">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c1cdc-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1cdc-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1cdc-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1cdc-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1cdc-126">See also</span></span>

- [<span data-ttu-id="c1cdc-127">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c1cdc-127">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
