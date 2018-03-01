---
title: "ICLRStrongName::StrongNameCompareAssemblies Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 96fbeccf76de87a3582bf8c2084d0ca9ad7d27f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="dcf4c-102">ICLRStrongName::StrongNameCompareAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dcf4c-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="dcf4c-103">İki derleme yalnızca güçlü ad imzaları tarafından farklı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="dcf4c-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcf4c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dcf4c-104">Syntax</span></span>  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dcf4c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dcf4c-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="dcf4c-106">[in] İlk derleme yolu.</span><span class="sxs-lookup"><span data-stu-id="dcf4c-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="dcf4c-107">[in] İkinci derleme yolu.</span><span class="sxs-lookup"><span data-stu-id="dcf4c-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="dcf4c-108">[out] Aşağıdaki değerlerden biri:</span><span class="sxs-lookup"><span data-stu-id="dcf4c-108">[out] One of the following values:</span></span>  
  
-   <span data-ttu-id="dcf4c-109">`SN_CMP_DIFFERENT`(0) - derlemeler farklı veri içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcf4c-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
-   <span data-ttu-id="dcf4c-110">`SN_CMP_IDENTICAL`(1) - derlemeler tam olarak aynı, kendi imzaları ve sağlama toplamı dahil olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcf4c-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   <span data-ttu-id="dcf4c-111">`SN_CMP_SIGONLY`(2) - derlemeler yalnızca imza ve sağlama toplamı tarafından farklı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcf4c-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dcf4c-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dcf4c-112">Return Value</span></span>  
 <span data-ttu-id="dcf4c-113">`S_OK`Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="dcf4c-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcf4c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dcf4c-114">Requirements</span></span>  
 <span data-ttu-id="dcf4c-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcf4c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcf4c-116">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="dcf4c-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="dcf4c-117">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="dcf4c-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcf4c-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcf4c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcf4c-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dcf4c-119">Remarks</span></span>  
 <span data-ttu-id="dcf4c-120">Bir derleme tanımlayıcı ad imzası derlemenin metin adı, sürüm, kültür ve ortak anahtar belirteci oluşur.</span><span class="sxs-lookup"><span data-stu-id="dcf4c-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcf4c-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dcf4c-121">See Also</span></span>  
 [<span data-ttu-id="dcf4c-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dcf4c-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
