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
ms.openlocfilehash: 8bd0292ddf22453f8892ed8bddd10c2144877097
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008527"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="39d22-102">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="39d22-102">LoadStringRC Function</span></span>
<span data-ttu-id="39d22-103">Geçerli iş parçacığının varsayılan kültürünü kullanarak bir HRESULT değerini bir hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="39d22-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="39d22-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="39d22-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39d22-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="39d22-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39d22-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="39d22-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="39d22-107">'ndaki HRESULT.</span><span class="sxs-lookup"><span data-stu-id="39d22-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="39d22-108">dışı Başarılı bir şekilde tamamlandıktan sonra hata iletisini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="39d22-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="39d22-109">'ndaki Hata iletisi arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="39d22-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="39d22-110">'ndaki LIP.</span><span class="sxs-lookup"><span data-stu-id="39d22-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39d22-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="39d22-111">Return Value</span></span>  
 <span data-ttu-id="39d22-112">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="39d22-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="39d22-113">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="39d22-113">Return code</span></span>|<span data-ttu-id="39d22-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39d22-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="39d22-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="39d22-115">S_OK</span></span>|<span data-ttu-id="39d22-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="39d22-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="39d22-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="39d22-117">E_INVALIDARG</span></span>|<span data-ttu-id="39d22-118">`szBuffer`null veya `iMax` sıfır (0).</span><span class="sxs-lookup"><span data-stu-id="39d22-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39d22-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39d22-119">Remarks</span></span>  
 <span data-ttu-id="39d22-120">Yöntem başarıyla tamamlanmazsa `szBuffer` boş bir dize içerir.</span><span class="sxs-lookup"><span data-stu-id="39d22-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39d22-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39d22-121">Requirements</span></span>  
 <span data-ttu-id="39d22-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39d22-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39d22-123">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="39d22-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="39d22-124">**Kitaplık:** MSCorEE. dll ve mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="39d22-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="39d22-125">.NET Framework doğru sürümünü hedefliyorsanız emin olmak için mscorwks. dll yerine MSCorEE. dll kullanın.</span><span class="sxs-lookup"><span data-stu-id="39d22-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="39d22-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39d22-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39d22-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39d22-127">See also</span></span>

- [<span data-ttu-id="39d22-128">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="39d22-128">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)
- [<span data-ttu-id="39d22-129">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="39d22-129">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
