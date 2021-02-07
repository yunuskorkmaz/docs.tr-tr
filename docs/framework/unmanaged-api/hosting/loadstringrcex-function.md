---
description: 'Daha fazla bilgi edinin: LoadStringRCEx Işlevi'
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
ms.openlocfilehash: d3fe4b97014e5093dd8d209a5e27bac4ed7b879f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679928"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="5b7b9-103">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="5b7b9-103">LoadStringRCEx Function</span></span>

<span data-ttu-id="5b7b9-104">Belirtilen kültür için bir HRESULT değerini uygun bir hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="5b7b9-104">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="5b7b9-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="5b7b9-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b7b9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b7b9-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5b7b9-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5b7b9-107">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="5b7b9-108">'ndaki Bir kültür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="5b7b9-108">[in] A culture identifier.</span></span> <span data-ttu-id="5b7b9-109">Varsayılan kültürü kullanmak için-1 ' i geçirin `lcid` .</span><span class="sxs-lookup"><span data-stu-id="5b7b9-109">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="5b7b9-110">'ndaki HRESULT.</span><span class="sxs-lookup"><span data-stu-id="5b7b9-110">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="5b7b9-111">dışı Başarılı bir şekilde tamamlandıktan sonra hata iletisini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="5b7b9-111">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="5b7b9-112">'ndaki Hata iletisi arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="5b7b9-112">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="5b7b9-113">'ndaki LIP.</span><span class="sxs-lookup"><span data-stu-id="5b7b9-113">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="5b7b9-114">dışı Hata iletisinin uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5b7b9-114">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b7b9-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5b7b9-115">Return Value</span></span>  

 <span data-ttu-id="5b7b9-116">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="5b7b9-116">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="5b7b9-117">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="5b7b9-117">Return code</span></span>|<span data-ttu-id="5b7b9-118">Description</span><span class="sxs-lookup"><span data-stu-id="5b7b9-118">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="5b7b9-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="5b7b9-119">S_OK</span></span>|<span data-ttu-id="5b7b9-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="5b7b9-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="5b7b9-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5b7b9-121">E_INVALIDARG</span></span>|<span data-ttu-id="5b7b9-122">`szBuffer` null veya `iMax` sıfır (0).</span><span class="sxs-lookup"><span data-stu-id="5b7b9-122">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b7b9-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b7b9-123">Remarks</span></span>  

 <span data-ttu-id="5b7b9-124">Yöntem başarıyla tamamlanmazsa `szBuffer` boş bir dize içerir.</span><span class="sxs-lookup"><span data-stu-id="5b7b9-124">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b7b9-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b7b9-125">Requirements</span></span>  

 <span data-ttu-id="5b7b9-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b7b9-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b7b9-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5b7b9-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b7b9-128">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5b7b9-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b7b9-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b7b9-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b7b9-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b7b9-130">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5b7b9-131">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="5b7b9-131">LoadStringRC Function</span></span>](loadstringrc-function.md)
- [<span data-ttu-id="5b7b9-132">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5b7b9-132">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
