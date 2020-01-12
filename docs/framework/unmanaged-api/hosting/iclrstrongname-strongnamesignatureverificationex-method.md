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
ms.openlocfilehash: fbc9ea6aab9f0c3d9be95e6affcd04342ce4c5cc
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901070"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="f1cde-102">ICLRStrongName::StrongNameSignatureVerificationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1cde-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>
<span data-ttu-id="f1cde-103">Belirtilen yoldaki Derleme bildiriminin bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f1cde-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1cde-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1cde-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1cde-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1cde-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="f1cde-106">'ndaki Doğrulanacak derleme için taşınabilir yürütülebilir (. exe veya. dll) dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="f1cde-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="f1cde-107">[in] kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulama gerçekleştirmek için `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="f1cde-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="f1cde-108">[out] tanımlayıcı ad imzası doğrulandıysa `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="f1cde-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="f1cde-109">Ayrıca, kayıt defteri ayarları nedeniyle doğrulama başarılı olduysa, `pfWasVerified` `false` olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f1cde-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1cde-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f1cde-110">Return Value</span></span>  
 <span data-ttu-id="f1cde-111">doğrulama başarılı olduysa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="f1cde-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1cde-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1cde-112">Remarks</span></span>  
 <span data-ttu-id="f1cde-113">[ICLRStrongName:: Strongnamesignaturedoğrulamaları Icationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) yöntemi [ICLRStrongName:: Strongnamesignaturedoğrulama](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) yöntemine benzer bir yetenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1cde-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="f1cde-114">Ancak, [ICLRStrongName:: Strongnamesignaturedoğrulamaları Icationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) için ikinci giriş parametresi ve çıkış parametresi `DWORD`yerine `BOOLEAN` türündedir.</span><span class="sxs-lookup"><span data-stu-id="f1cde-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1cde-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1cde-115">Requirements</span></span>  
 <span data-ttu-id="f1cde-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1cde-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1cde-117">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="f1cde-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f1cde-118">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="f1cde-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1cde-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1cde-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1cde-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1cde-120">See also</span></span>

- [<span data-ttu-id="f1cde-121">StrongNameSignatureVerification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1cde-121">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="f1cde-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1cde-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
