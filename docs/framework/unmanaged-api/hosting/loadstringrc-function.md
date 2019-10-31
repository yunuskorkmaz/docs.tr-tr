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
ms.openlocfilehash: 66d4c14234c7929af443922f86098b46a4aa6eb7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122011"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="d0e01-102">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="d0e01-102">LoadStringRC Function</span></span>
<span data-ttu-id="d0e01-103">Geçerli iş parçacığının varsayılan kültürünü kullanarak bir HRESULT değerini bir hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="d0e01-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="d0e01-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="d0e01-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0e01-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0e01-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0e01-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0e01-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="d0e01-107">'ndaki HRESULT.</span><span class="sxs-lookup"><span data-stu-id="d0e01-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="d0e01-108">dışı Başarılı bir şekilde tamamlandıktan sonra hata iletisini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="d0e01-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="d0e01-109">'ndaki Hata iletisi arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="d0e01-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="d0e01-110">'ndaki LIP.</span><span class="sxs-lookup"><span data-stu-id="d0e01-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0e01-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d0e01-111">Return Value</span></span>  
 <span data-ttu-id="d0e01-112">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0e01-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="d0e01-113">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="d0e01-113">Return code</span></span>|<span data-ttu-id="d0e01-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0e01-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d0e01-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d0e01-115">S_OK</span></span>|<span data-ttu-id="d0e01-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="d0e01-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="d0e01-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d0e01-117">E_INVALIDARG</span></span>|<span data-ttu-id="d0e01-118">`szBuffer` null veya `iMax` sıfır (0).</span><span class="sxs-lookup"><span data-stu-id="d0e01-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0e01-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0e01-119">Remarks</span></span>  
 <span data-ttu-id="d0e01-120">Yöntem başarıyla tamamlanmazsa, `szBuffer` boş bir dize içerir.</span><span class="sxs-lookup"><span data-stu-id="d0e01-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0e01-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0e01-121">Requirements</span></span>  
 <span data-ttu-id="d0e01-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0e01-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0e01-123">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d0e01-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0e01-124">**Kitaplık:** MSCorEE. dll ve mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="d0e01-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="d0e01-125">.NET Framework doğru sürümünü hedefliyorsanız emin olmak için mscorwks. dll yerine MSCorEE. dll kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0e01-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="d0e01-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0e01-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e01-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0e01-127">See also</span></span>

- [<span data-ttu-id="d0e01-128">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="d0e01-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [<span data-ttu-id="d0e01-129">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d0e01-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
