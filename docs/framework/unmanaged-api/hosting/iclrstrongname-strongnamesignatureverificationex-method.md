---
title: ICLRStrongName::StrongNameSignatureVerificationEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da9b0fd4fd7c7eadf09f0b76a17e60b1840fdf48
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724223"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="d8ec4-102">ICLRStrongName::StrongNameSignatureVerificationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8ec4-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>
<span data-ttu-id="d8ec4-103">Sağlanan yol, derleme bildirimi tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d8ec4-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8ec4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8ec4-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8ec4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8ec4-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d8ec4-106">[in] Taşınabilir yürütülebilir (.exe veya .dll) dosyası doğrulanması derleme yolu.</span><span class="sxs-lookup"><span data-stu-id="d8ec4-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="d8ec4-107">[in] `true` , olsa bile gerekli kayıt defteri ayarlarını geçersiz kılmak; Aksi takdirde, doğrulamanın `false`.</span><span class="sxs-lookup"><span data-stu-id="d8ec4-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="d8ec4-108">[out] `true` tanımlayıcı ad imzası, doğrulanmış; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="d8ec4-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="d8ec4-109">`pfWasVerified` Ayrıca kümesine `false` kayıt defteri ayarları nedeniyle doğrulama başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="d8ec4-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8ec4-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d8ec4-110">Return Value</span></span>  
 <span data-ttu-id="d8ec4-111">`S_OK` doğrulama başarılı olduysa; Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="d8ec4-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8ec4-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8ec4-112">Remarks</span></span>  
 <span data-ttu-id="d8ec4-113">[Iclrstrongname::strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) yöntemi benzer bir yetenek sağlar [Iclrstrongname::strongnamesignatureverification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d8ec4-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="d8ec4-114">Ancak, giriş parametresi ve çıkış parametresi için ikinci [Iclrstrongname::strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) türü `BOOLEAN` yerine `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="d8ec4-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8ec4-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8ec4-115">Requirements</span></span>  
 <span data-ttu-id="d8ec4-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ec4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ec4-117">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d8ec4-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d8ec4-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d8ec4-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8ec4-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ec4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ec4-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8ec4-120">See Also</span></span>  
 [<span data-ttu-id="d8ec4-121">StrongNameSignatureVerification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8ec4-121">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="d8ec4-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8ec4-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
