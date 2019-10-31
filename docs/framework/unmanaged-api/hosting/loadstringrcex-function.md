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
ms.openlocfilehash: 68332aee895f012bcf6ab6a72936c8dddc7f28a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122044"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="8725f-102">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="8725f-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="8725f-103">Belirtilen kültür için bir HRESULT değerini uygun bir hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="8725f-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="8725f-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="8725f-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8725f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8725f-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8725f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8725f-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="8725f-107">'ndaki Bir kültür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="8725f-107">[in] A culture identifier.</span></span> <span data-ttu-id="8725f-108">`lcid` için-1 ' i varsayılan kültürü kullanacak şekilde geçirin.</span><span class="sxs-lookup"><span data-stu-id="8725f-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="8725f-109">'ndaki HRESULT.</span><span class="sxs-lookup"><span data-stu-id="8725f-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="8725f-110">dışı Başarılı bir şekilde tamamlandıktan sonra hata iletisini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="8725f-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="8725f-111">'ndaki Hata iletisi arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="8725f-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="8725f-112">'ndaki LIP.</span><span class="sxs-lookup"><span data-stu-id="8725f-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="8725f-113">dışı Hata iletisinin uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8725f-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8725f-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8725f-114">Return Value</span></span>  
 <span data-ttu-id="8725f-115">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="8725f-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="8725f-116">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="8725f-116">Return code</span></span>|<span data-ttu-id="8725f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8725f-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="8725f-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="8725f-118">S_OK</span></span>|<span data-ttu-id="8725f-119">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="8725f-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="8725f-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8725f-120">E_INVALIDARG</span></span>|<span data-ttu-id="8725f-121">`szBuffer` null veya `iMax` sıfır (0).</span><span class="sxs-lookup"><span data-stu-id="8725f-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8725f-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8725f-122">Remarks</span></span>  
 <span data-ttu-id="8725f-123">Yöntem başarıyla tamamlanmazsa, `szBuffer` boş bir dize içerir.</span><span class="sxs-lookup"><span data-stu-id="8725f-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8725f-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8725f-124">Requirements</span></span>  
 <span data-ttu-id="8725f-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8725f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8725f-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8725f-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8725f-127">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8725f-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8725f-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8725f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8725f-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8725f-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8725f-130">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="8725f-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="8725f-131">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="8725f-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
