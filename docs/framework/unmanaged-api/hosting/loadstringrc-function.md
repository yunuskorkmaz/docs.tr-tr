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
ms.openlocfilehash: 56ae7b7cf3b577bfe41ebd0bdd98e0da68047b44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176246"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="50344-102">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="50344-102">LoadStringRC Function</span></span>
<span data-ttu-id="50344-103">Geçerli iş parçacığının varsayılan kültürünü kullanarak bir HRESULT değerini hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="50344-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="50344-104">Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="50344-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50344-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50344-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50344-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50344-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="50344-107">[içinde] Bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="50344-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="50344-108">[çıkış] Başarılı bir şekilde tamamlandıktan sonra hata iletisi içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="50344-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="50344-109">[içinde] Hata iletisi arabelleği boyutu.</span><span class="sxs-lookup"><span data-stu-id="50344-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="50344-110">[içinde] Göz ardı.</span><span class="sxs-lookup"><span data-stu-id="50344-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50344-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="50344-111">Return Value</span></span>  
 <span data-ttu-id="50344-112">Bu yöntem, aşağıdaki değerlere ek olarak WinError.h'de tanımlandığı şekilde standart Bileşen Nesne Modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="50344-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="50344-113">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="50344-113">Return code</span></span>|<span data-ttu-id="50344-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50344-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="50344-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="50344-115">S_OK</span></span>|<span data-ttu-id="50344-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="50344-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="50344-117">E_ınvalıdarg</span><span class="sxs-lookup"><span data-stu-id="50344-117">E_INVALIDARG</span></span>|<span data-ttu-id="50344-118">`szBuffer`null veya `iMax` sıfır (0) olduğunu.</span><span class="sxs-lookup"><span data-stu-id="50344-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50344-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50344-119">Remarks</span></span>  
 <span data-ttu-id="50344-120">Yöntem başarıyla tamamlanmamışsa, `szBuffer` boş bir dize içerir.</span><span class="sxs-lookup"><span data-stu-id="50344-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50344-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50344-121">Requirements</span></span>  
 <span data-ttu-id="50344-122">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50344-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50344-123">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="50344-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50344-124">**Kütüphane:** MSCorEE.dll ve Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="50344-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="50344-125">.NET Framework'ün doğru sürümünü hedeflediğinizden emin olmak için Mscorwks.dll yerine MSCorEE.dll'yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="50344-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="50344-126">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50344-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50344-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50344-127">See also</span></span>

- [<span data-ttu-id="50344-128">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="50344-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [<span data-ttu-id="50344-129">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="50344-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
