---
title: ICLRStrongName::StrongNameCompareAssemblies Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
ms.openlocfilehash: ddcbe84053aa7f4cafd81e905f8aef988f92875e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685709"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="d57fd-102">ICLRStrongName::StrongNameCompareAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d57fd-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>

<span data-ttu-id="d57fd-103">İki derlemenin yalnızca kendi tanımlayıcı ad imzalarına göre farklı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d57fd-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d57fd-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d57fd-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d57fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d57fd-105">Parameters</span></span>  

 `wszAssembly1`  
 <span data-ttu-id="d57fd-106">'ndaki İlk derlemenin yolu.</span><span class="sxs-lookup"><span data-stu-id="d57fd-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="d57fd-107">'ndaki İkinci derlemenin yolu.</span><span class="sxs-lookup"><span data-stu-id="d57fd-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="d57fd-108">dışı Aşağıdaki değerlerden biri:</span><span class="sxs-lookup"><span data-stu-id="d57fd-108">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="d57fd-109">`SN_CMP_DIFFERENT` (0)-derlemelerin farklı veriler içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d57fd-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="d57fd-110">`SN_CMP_IDENTICAL` (1)-derlemelerin imzaları ve sağlama toplamı dahil olmak üzere tam olarak aynı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d57fd-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="d57fd-111">`SN_CMP_SIGONLY` (2)-derlemelerin yalnızca imzaya ve sağlama toplamına göre farklı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d57fd-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d57fd-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d57fd-112">Return Value</span></span>  

 <span data-ttu-id="d57fd-113">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="d57fd-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d57fd-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d57fd-114">Requirements</span></span>  

 <span data-ttu-id="d57fd-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d57fd-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d57fd-116">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d57fd-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d57fd-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d57fd-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d57fd-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d57fd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d57fd-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d57fd-119">Remarks</span></span>  

 <span data-ttu-id="d57fd-120">Bir derlemenin tanımlayıcı ad imzası, derlemenin metin adı, sürüm, kültür ve ortak anahtar belirtecinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="d57fd-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d57fd-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d57fd-121">See also</span></span>

- [<span data-ttu-id="d57fd-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d57fd-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
