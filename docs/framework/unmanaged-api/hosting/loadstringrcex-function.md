---
title: "LoadStringRCEx İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadStringRCEx
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: LoadStringRCEx
helpviewer_keywords: LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3467ebcd0b821c2313f3535c5b594ef664546e4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="f686d-102">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="f686d-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="f686d-103">Uygun bir hata iletisi belirtilen kültür için HRESULT değerine dönüşür.</span><span class="sxs-lookup"><span data-stu-id="f686d-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="f686d-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f686d-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f686d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f686d-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="f686d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f686d-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="f686d-107">[in] Bir kültür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f686d-107">[in] A culture identifier.</span></span> <span data-ttu-id="f686d-108">-1 geçirmek `lcid` varsayılan kültürü kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="f686d-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="f686d-109">[in] HRESULT.</span><span class="sxs-lookup"><span data-stu-id="f686d-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="f686d-110">[out] İşlem başarıyla tamamlandıktan sonra hata iletisini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="f686d-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="f686d-111">[in] Hata iletisi arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="f686d-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="f686d-112">[in] Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="f686d-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="f686d-113">[out] Hata iletisi uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f686d-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f686d-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f686d-114">Return Value</span></span>  
 <span data-ttu-id="f686d-115">Bu yöntem standart COM hata kodları, ek olarak aşağıdaki değerleri Winerror.h'de içinde tanımlandığı şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="f686d-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="f686d-116">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="f686d-116">Return code</span></span>|<span data-ttu-id="f686d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f686d-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f686d-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="f686d-118">S_OK</span></span>|<span data-ttu-id="f686d-119">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="f686d-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="f686d-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f686d-120">E_INVALIDARG</span></span>|<span data-ttu-id="f686d-121">`szBuffer`null, veya `iMax` sıfır (0).</span><span class="sxs-lookup"><span data-stu-id="f686d-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f686d-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f686d-122">Remarks</span></span>  
 <span data-ttu-id="f686d-123">Yöntem başarıyla tamamlanmazsa `szBuffer` boş bir dize içeriyor.</span><span class="sxs-lookup"><span data-stu-id="f686d-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f686d-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f686d-124">Requirements</span></span>  
 <span data-ttu-id="f686d-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f686d-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f686d-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f686d-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f686d-127">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f686d-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f686d-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f686d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f686d-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f686d-129">See Also</span></span>  
 <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="f686d-130">LoadStringRC işlevi</span><span class="sxs-lookup"><span data-stu-id="f686d-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 [<span data-ttu-id="f686d-131">Kullanım dışı CLR barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="f686d-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
