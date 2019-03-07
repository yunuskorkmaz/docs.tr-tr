---
title: LoadStringRC İşlevi
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e020b65966dc03bf326220ab0bab26bc61155c0c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485492"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="40e2a-102">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="40e2a-102">LoadStringRC Function</span></span>
<span data-ttu-id="40e2a-103">Geçerli iş parçacığının varsayılan kültürünü kullanarak, bir HRESULT değerini hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="40e2a-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="40e2a-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40e2a-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40e2a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40e2a-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40e2a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40e2a-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="40e2a-107">[in] HRESULT.</span><span class="sxs-lookup"><span data-stu-id="40e2a-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="40e2a-108">[out] Başarılı tamamlandığında hata iletisini içeren bir arabelleği.</span><span class="sxs-lookup"><span data-stu-id="40e2a-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="40e2a-109">[in] Hata iletisi arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="40e2a-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="40e2a-110">[in] Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="40e2a-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40e2a-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="40e2a-111">Return Value</span></span>  
 <span data-ttu-id="40e2a-112">Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Wınerror içinde tanımlanan döndürür.</span><span class="sxs-lookup"><span data-stu-id="40e2a-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="40e2a-113">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="40e2a-113">Return code</span></span>|<span data-ttu-id="40e2a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40e2a-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="40e2a-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="40e2a-115">S_OK</span></span>|<span data-ttu-id="40e2a-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="40e2a-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="40e2a-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="40e2a-117">E_INVALIDARG</span></span>|<span data-ttu-id="40e2a-118">`szBuffer` null veya `iMax` sıfır (0).</span><span class="sxs-lookup"><span data-stu-id="40e2a-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40e2a-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40e2a-119">Remarks</span></span>  
 <span data-ttu-id="40e2a-120">Yöntemi başarıyla tamamlanmazsa `szBuffer` boş bir dize içeriyor.</span><span class="sxs-lookup"><span data-stu-id="40e2a-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40e2a-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40e2a-121">Requirements</span></span>  
 <span data-ttu-id="40e2a-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40e2a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40e2a-123">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="40e2a-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40e2a-124">**Kitaplığı:** MSCorEE.dll and Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="40e2a-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="40e2a-125">MSCorEE.dll yerine Mscorwks.dll doğru .NET Framework sürümünü hedefleyen emin olmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="40e2a-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="40e2a-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40e2a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e2a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40e2a-127">See also</span></span>
- [<span data-ttu-id="40e2a-128">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="40e2a-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [<span data-ttu-id="40e2a-129">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="40e2a-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
