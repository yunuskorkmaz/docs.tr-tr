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
ms.openlocfilehash: e2003ce78f04b101fe093867e0820f9c3840151a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762714"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="43380-102">ICLRStrongName::StrongNameSignatureVerificationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43380-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>
<span data-ttu-id="43380-103">Belirtilen yoldaki Derleme bildiriminin bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="43380-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43380-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="43380-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43380-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43380-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="43380-106">'ndaki Doğrulanacak derleme için taşınabilir yürütülebilir (. exe veya. dll) dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="43380-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="43380-107">[in] `true` doğrulama gerçekleştirmek için, kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="43380-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="43380-108">[out] `true` tanımlayıcı ad imzası doğrulandıysa; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="43380-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="43380-109">`pfWasVerified`, `false` kayıt defteri ayarları nedeniyle doğrulama başarılı olduysa olarak da ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="43380-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43380-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="43380-110">Return Value</span></span>  
 <span data-ttu-id="43380-111">`S_OK`doğrulama başarılı olduysa, Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="43380-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43380-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43380-112">Remarks</span></span>  
 <span data-ttu-id="43380-113">[ICLRStrongName:: Strongnamesignaturedoğrulamaları Icationex](iclrstrongname-strongnamesignatureverificationex-method.md) yöntemi [ICLRStrongName:: Strongnamesignaturedoğrulama](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) yöntemine benzer bir yetenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="43380-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="43380-114">Ancak, ikinci giriş parametresi ve [ICLRStrongName:: Strongnamesignaturedoğrulamaları Icationex](iclrstrongname-strongnamesignatureverificationex-method.md) için çıkış parametresi `BOOLEAN` yerine türüdür `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="43380-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43380-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43380-115">Requirements</span></span>  
 <span data-ttu-id="43380-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43380-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43380-117">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="43380-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="43380-118">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="43380-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43380-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43380-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43380-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43380-120">See also</span></span>

- [<span data-ttu-id="43380-121">StrongNameSignatureVerification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43380-121">StrongNameSignatureVerification Method</span></span>](iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="43380-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43380-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
