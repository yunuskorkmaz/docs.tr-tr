---
title: StrongNameSignatureVerificationEx2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e47c2ac69317b2d2db489dce9a0102b5fe304c05
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856883"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="b999c-102">StrongNameSignatureVerificationEx2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b999c-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="b999c-103">Kesin adlandırılmış derlemenin imzayı doğrular ve ECMA anahtarından bir eşleme için gerçek bir anahtar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b999c-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b999c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b999c-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b999c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b999c-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b999c-106">[in] Taşınabilir yürütülebilir (.exe veya .dll) dosyası doğrulanması derleme yolu.</span><span class="sxs-lookup"><span data-stu-id="b999c-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="b999c-107">[in] `true` , olsa bile gerekli kayıt defteri ayarlarını geçersiz kılmak; Aksi takdirde, doğrulamanın `false`.</span><span class="sxs-lookup"><span data-stu-id="b999c-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="b999c-108">[in] Eşleme için bir işaretçi gerçek anahtarı ECMA ortak anahtarından doğrulama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b999c-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="b999c-109">[in] Gerçek ECMA ortak anahtarın uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="b999c-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="b999c-110">[out] `true` tanımlayıcı ad imzası, doğrulanmış; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="b999c-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="b999c-111">Bu parametre aynı zamanda kümesine `false` kayıt defteri ayarları nedeniyle doğrulama başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="b999c-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b999c-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b999c-112">Return Value</span></span>  
 <span data-ttu-id="b999c-113">`S_OK` doğrulama başarılı olduysa; Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="b999c-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b999c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b999c-114">Requirements</span></span>  
 <span data-ttu-id="b999c-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b999c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b999c-116">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b999c-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b999c-117">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b999c-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b999c-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b999c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b999c-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b999c-119">See Also</span></span>  
 [<span data-ttu-id="b999c-120">StrongNameSignatureVerification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b999c-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="b999c-121">StrongNameSignatureVerificationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b999c-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="b999c-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b999c-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
