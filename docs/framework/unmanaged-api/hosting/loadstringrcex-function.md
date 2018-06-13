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
ms.openlocfilehash: 38c942b9a94c83f5a3316cf3ae3ccbbad2b0ec69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444323"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="0d363-102">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="0d363-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="0d363-103">Uygun bir hata iletisi belirtilen kültür için HRESULT değerine dönüşür.</span><span class="sxs-lookup"><span data-stu-id="0d363-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="0d363-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0d363-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d363-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d363-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="0d363-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d363-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="0d363-107">[in] Bir kültür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="0d363-107">[in] A culture identifier.</span></span> <span data-ttu-id="0d363-108">-1 geçirmek `lcid` varsayılan kültürü kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="0d363-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="0d363-109">[in] HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0d363-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="0d363-110">[out] İşlem başarıyla tamamlandıktan sonra hata iletisini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="0d363-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="0d363-111">[in] Hata iletisi arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="0d363-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="0d363-112">[in] Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="0d363-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="0d363-113">[out] Hata iletisi uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0d363-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d363-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0d363-114">Return Value</span></span>  
 <span data-ttu-id="0d363-115">Bu yöntem standart COM hata kodları, ek olarak aşağıdaki değerleri Winerror.h'de içinde tanımlandığı şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d363-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="0d363-116">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="0d363-116">Return code</span></span>|<span data-ttu-id="0d363-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d363-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="0d363-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="0d363-118">S_OK</span></span>|<span data-ttu-id="0d363-119">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="0d363-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="0d363-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0d363-120">E_INVALIDARG</span></span>|<span data-ttu-id="0d363-121">`szBuffer` null, veya `iMax` sıfır (0).</span><span class="sxs-lookup"><span data-stu-id="0d363-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d363-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d363-122">Remarks</span></span>  
 <span data-ttu-id="0d363-123">Yöntem başarıyla tamamlanmazsa `szBuffer` boş bir dize içeriyor.</span><span class="sxs-lookup"><span data-stu-id="0d363-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d363-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d363-124">Requirements</span></span>  
 <span data-ttu-id="0d363-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d363-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d363-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0d363-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d363-127">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d363-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d363-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d363-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d363-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0d363-129">See Also</span></span>  
 <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="0d363-130">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="0d363-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 [<span data-ttu-id="0d363-131">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0d363-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
