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
ms.openlocfilehash: 4a0cac77d7bf7611acf6042298bfe6814d8f4352
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768445"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="5ac41-102">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="5ac41-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="5ac41-103">HRESULT değerini belirtilen kültür için uygun hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="5ac41-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="5ac41-104">Bu işlev .NET Framework 4'te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="5ac41-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ac41-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ac41-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5ac41-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ac41-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="5ac41-107">[in] Bir kültür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="5ac41-107">[in] A culture identifier.</span></span> <span data-ttu-id="5ac41-108">-1 geçirmek `lcid` varsayılan kültür kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="5ac41-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="5ac41-109">[in] HRESULT.</span><span class="sxs-lookup"><span data-stu-id="5ac41-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="5ac41-110">[out] Başarılı tamamlandığında hata iletisini içeren bir arabelleği.</span><span class="sxs-lookup"><span data-stu-id="5ac41-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="5ac41-111">[in] Hata iletisi arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="5ac41-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="5ac41-112">[in] Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="5ac41-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="5ac41-113">[out] Hata iletisi uzunluğu bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5ac41-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ac41-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5ac41-114">Return Value</span></span>  
 <span data-ttu-id="5ac41-115">Bu yöntem, ek olarak aşağıdaki değerleri Wınerror içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="5ac41-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="5ac41-116">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="5ac41-116">Return code</span></span>|<span data-ttu-id="5ac41-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ac41-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="5ac41-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ac41-118">S_OK</span></span>|<span data-ttu-id="5ac41-119">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="5ac41-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="5ac41-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5ac41-120">E_INVALIDARG</span></span>|<span data-ttu-id="5ac41-121">`szBuffer` null ise veya `iMax` sıfır (0).</span><span class="sxs-lookup"><span data-stu-id="5ac41-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ac41-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ac41-122">Remarks</span></span>  
 <span data-ttu-id="5ac41-123">Yöntemi başarıyla tamamlanmazsa `szBuffer` boş bir dize içeriyor.</span><span class="sxs-lookup"><span data-stu-id="5ac41-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ac41-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ac41-124">Requirements</span></span>  
 <span data-ttu-id="5ac41-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ac41-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ac41-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5ac41-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ac41-127">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5ac41-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ac41-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ac41-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ac41-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ac41-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5ac41-130">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="5ac41-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="5ac41-131">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5ac41-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
