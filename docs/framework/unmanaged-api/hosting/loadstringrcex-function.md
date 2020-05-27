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
ms.openlocfilehash: a05cbe985c2cfebb67756fdfb54398b36e87f441
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008525"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="05739-102">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="05739-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="05739-103">Belirtilen kültür için bir HRESULT değerini uygun bir hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="05739-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="05739-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="05739-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05739-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="05739-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="05739-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05739-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="05739-107">'ndaki Bir kültür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="05739-107">[in] A culture identifier.</span></span> <span data-ttu-id="05739-108">Varsayılan kültürü kullanmak için-1 ' i geçirin `lcid` .</span><span class="sxs-lookup"><span data-stu-id="05739-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="05739-109">'ndaki HRESULT.</span><span class="sxs-lookup"><span data-stu-id="05739-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="05739-110">dışı Başarılı bir şekilde tamamlandıktan sonra hata iletisini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="05739-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="05739-111">'ndaki Hata iletisi arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="05739-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="05739-112">'ndaki LIP.</span><span class="sxs-lookup"><span data-stu-id="05739-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="05739-113">dışı Hata iletisinin uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="05739-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05739-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="05739-114">Return Value</span></span>  
 <span data-ttu-id="05739-115">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="05739-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="05739-116">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="05739-116">Return code</span></span>|<span data-ttu-id="05739-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05739-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="05739-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="05739-118">S_OK</span></span>|<span data-ttu-id="05739-119">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="05739-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="05739-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="05739-120">E_INVALIDARG</span></span>|<span data-ttu-id="05739-121">`szBuffer`null veya `iMax` sıfır (0).</span><span class="sxs-lookup"><span data-stu-id="05739-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05739-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05739-122">Remarks</span></span>  
 <span data-ttu-id="05739-123">Yöntem başarıyla tamamlanmazsa `szBuffer` boş bir dize içerir.</span><span class="sxs-lookup"><span data-stu-id="05739-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05739-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05739-124">Requirements</span></span>  
 <span data-ttu-id="05739-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05739-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05739-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="05739-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05739-127">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="05739-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05739-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05739-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05739-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05739-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="05739-130">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="05739-130">LoadStringRC Function</span></span>](loadstringrc-function.md)
- [<span data-ttu-id="05739-131">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="05739-131">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
