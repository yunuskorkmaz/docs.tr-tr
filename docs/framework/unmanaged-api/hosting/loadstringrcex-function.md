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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c3185bdc0776d6536458ce03c348ed77b8ba0b9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499101"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="34552-102">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="34552-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="34552-103">HRESULT değerini belirtilen kültür için uygun hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="34552-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="34552-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34552-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34552-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34552-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,   
    [in]  UINT    iResouceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet,   
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34552-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34552-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="34552-107">[in] Bir kültür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="34552-107">[in] A culture identifier.</span></span> <span data-ttu-id="34552-108">-1 geçirmek `lcid` varsayılan kültür kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="34552-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="34552-109">[in] HRESULT.</span><span class="sxs-lookup"><span data-stu-id="34552-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="34552-110">[out] Başarılı tamamlandığında hata iletisini içeren bir arabelleği.</span><span class="sxs-lookup"><span data-stu-id="34552-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="34552-111">[in] Hata iletisi arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="34552-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="34552-112">[in] Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="34552-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="34552-113">[out] Hata iletisi uzunluğu bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="34552-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34552-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="34552-114">Return Value</span></span>  
 <span data-ttu-id="34552-115">Bu yöntem, ek olarak aşağıdaki değerleri Wınerror içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="34552-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="34552-116">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="34552-116">Return code</span></span>|<span data-ttu-id="34552-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34552-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="34552-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="34552-118">S_OK</span></span>|<span data-ttu-id="34552-119">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="34552-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="34552-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="34552-120">E_INVALIDARG</span></span>|<span data-ttu-id="34552-121">`szBuffer` null ise veya `iMax` sıfır (0).</span><span class="sxs-lookup"><span data-stu-id="34552-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34552-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34552-122">Remarks</span></span>  
 <span data-ttu-id="34552-123">Yöntemi başarıyla tamamlanmazsa `szBuffer` boş bir dize içeriyor.</span><span class="sxs-lookup"><span data-stu-id="34552-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34552-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34552-124">Requirements</span></span>  
 <span data-ttu-id="34552-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34552-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34552-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="34552-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34552-127">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="34552-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34552-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34552-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34552-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34552-129">See also</span></span>
- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="34552-130">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="34552-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="34552-131">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="34552-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
