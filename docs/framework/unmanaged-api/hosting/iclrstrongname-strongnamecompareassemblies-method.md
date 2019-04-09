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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63d4b885b6968b800bc965a9be1ec6b795a42220
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140666"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="aafc2-102">ICLRStrongName::StrongNameCompareAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aafc2-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="aafc2-103">İki derlemenin yalnızca tanımlayıcı ad imzaları tarafından farklı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="aafc2-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aafc2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aafc2-104">Syntax</span></span>  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aafc2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aafc2-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="aafc2-106">[in] İlk bütünleştirilmiş kod yolu.</span><span class="sxs-lookup"><span data-stu-id="aafc2-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="aafc2-107">[in] İkinci bütünleştirilmiş kod yolu.</span><span class="sxs-lookup"><span data-stu-id="aafc2-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="aafc2-108">[out] Aşağıdaki değerlerden biri:</span><span class="sxs-lookup"><span data-stu-id="aafc2-108">[out] One of the following values:</span></span>  
  
-   `SN_CMP_DIFFERENT` <span data-ttu-id="aafc2-109">(0) - derlemeleri farklı veri içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aafc2-109">(0) - Specifies that the assemblies contain different data.</span></span>  
  
-   `SN_CMP_IDENTICAL` <span data-ttu-id="aafc2-110">(1) - derlemeleri tam olarak aynı kendi imzaları ve sağlama toplamı dahil olmak üzere olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="aafc2-110">(1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   `SN_CMP_SIGONLY` <span data-ttu-id="aafc2-111">(2) - derlemeler yalnızca imza ve sağlama toplamı farklı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="aafc2-111">(2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aafc2-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aafc2-112">Return Value</span></span>  
 `S_OK` <span data-ttu-id="aafc2-113">yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="aafc2-113">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aafc2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aafc2-114">Requirements</span></span>  
 <span data-ttu-id="aafc2-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aafc2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aafc2-116">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="aafc2-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="aafc2-117">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="aafc2-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="aafc2-118">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="aafc2-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="remarks"></a><span data-ttu-id="aafc2-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aafc2-119">Remarks</span></span>  
 <span data-ttu-id="aafc2-120">Bir derlemenin tanımlayıcı ad imzası, derlemenin metin adı, sürüm, kültür ve ortak anahtar belirteci oluşur.</span><span class="sxs-lookup"><span data-stu-id="aafc2-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aafc2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aafc2-121">See also</span></span>

- [<span data-ttu-id="aafc2-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aafc2-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
