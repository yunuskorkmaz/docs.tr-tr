---
title: LoadStringRCEx İşlevi
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
ms.openlocfilehash: a300c2679ef11a84edb2ab89c8dea96e445c9ee3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177976"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="b1e13-102">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="b1e13-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="b1e13-103">HRESULT değerini belirtilen kültür için uygun bir hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="b1e13-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="b1e13-104">Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b1e13-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1e13-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1e13-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,
    [in]  UINT    iResouceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet,
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1e13-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1e13-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="b1e13-107">[içinde] Bir kültür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="b1e13-107">[in] A culture identifier.</span></span> <span data-ttu-id="b1e13-108">Varsayılan kültürü `lcid` kullanmak için -1'i geç.</span><span class="sxs-lookup"><span data-stu-id="b1e13-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="b1e13-109">[içinde] Bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b1e13-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="b1e13-110">[çıkış] Başarılı bir şekilde tamamlandıktan sonra hata iletisi içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="b1e13-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="b1e13-111">[içinde] Hata iletisi arabelleği boyutu.</span><span class="sxs-lookup"><span data-stu-id="b1e13-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="b1e13-112">[içinde] Göz ardı.</span><span class="sxs-lookup"><span data-stu-id="b1e13-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="b1e13-113">[çıkış] Hata iletisinin uzunluğuna işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b1e13-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1e13-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b1e13-114">Return Value</span></span>  
 <span data-ttu-id="b1e13-115">Bu yöntem, aşağıdaki değerlere ek olarak WinError.h'de tanımlandığı şekilde standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="b1e13-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="b1e13-116">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="b1e13-116">Return code</span></span>|<span data-ttu-id="b1e13-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1e13-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b1e13-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1e13-118">S_OK</span></span>|<span data-ttu-id="b1e13-119">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="b1e13-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="b1e13-120">E_ınvalıdarg</span><span class="sxs-lookup"><span data-stu-id="b1e13-120">E_INVALIDARG</span></span>|<span data-ttu-id="b1e13-121">`szBuffer`null veya `iMax` sıfır (0) ise.</span><span class="sxs-lookup"><span data-stu-id="b1e13-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1e13-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1e13-122">Remarks</span></span>  
 <span data-ttu-id="b1e13-123">Yöntem başarıyla tamamlanmamışsa, `szBuffer` boş bir dize içerir.</span><span class="sxs-lookup"><span data-stu-id="b1e13-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1e13-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1e13-124">Requirements</span></span>  
 <span data-ttu-id="b1e13-125">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1e13-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1e13-126">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b1e13-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1e13-127">**Kütüphane:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b1e13-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1e13-128">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1e13-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1e13-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1e13-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b1e13-130">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="b1e13-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="b1e13-131">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b1e13-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
