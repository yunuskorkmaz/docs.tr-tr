---
description: 'Daha fazla bilgi edinin: LoadStringRC Işlevi'
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
ms.openlocfilehash: 188597f9dc21b6a67fb84e91cd66b50ba5a514f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679931"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="a2ff9-103">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="a2ff9-103">LoadStringRC Function</span></span>

<span data-ttu-id="a2ff9-104">Geçerli iş parçacığının varsayılan kültürünü kullanarak bir HRESULT değerini bir hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="a2ff9-104">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="a2ff9-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="a2ff9-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2ff9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2ff9-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2ff9-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2ff9-107">Parameters</span></span>  

 `iResourceID`  
 <span data-ttu-id="a2ff9-108">'ndaki HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a2ff9-108">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="a2ff9-109">dışı Başarılı bir şekilde tamamlandıktan sonra hata iletisini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="a2ff9-109">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="a2ff9-110">'ndaki Hata iletisi arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="a2ff9-110">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="a2ff9-111">'ndaki LIP.</span><span class="sxs-lookup"><span data-stu-id="a2ff9-111">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2ff9-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a2ff9-112">Return Value</span></span>  

 <span data-ttu-id="a2ff9-113">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="a2ff9-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="a2ff9-114">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="a2ff9-114">Return code</span></span>|<span data-ttu-id="a2ff9-115">Description</span><span class="sxs-lookup"><span data-stu-id="a2ff9-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a2ff9-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2ff9-116">S_OK</span></span>|<span data-ttu-id="a2ff9-117">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="a2ff9-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="a2ff9-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a2ff9-118">E_INVALIDARG</span></span>|<span data-ttu-id="a2ff9-119">`szBuffer` null veya `iMax` sıfır (0).</span><span class="sxs-lookup"><span data-stu-id="a2ff9-119">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2ff9-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2ff9-120">Remarks</span></span>  

 <span data-ttu-id="a2ff9-121">Yöntem başarıyla tamamlanmazsa `szBuffer` boş bir dize içerir.</span><span class="sxs-lookup"><span data-stu-id="a2ff9-121">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2ff9-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2ff9-122">Requirements</span></span>  

 <span data-ttu-id="a2ff9-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2ff9-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2ff9-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a2ff9-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2ff9-125">**Kitaplık:** MSCorEE.dll ve Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="a2ff9-125">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="a2ff9-126">Doğru .NET Framework sürümünü hedefliyorsanız emin olmak için Mscorwks.dll yerine MSCorEE.dll kullanın.</span><span class="sxs-lookup"><span data-stu-id="a2ff9-126">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a2ff9-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2ff9-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ff9-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2ff9-128">See also</span></span>

- [<span data-ttu-id="a2ff9-129">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="a2ff9-129">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)
- [<span data-ttu-id="a2ff9-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a2ff9-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
