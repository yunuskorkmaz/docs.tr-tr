---
description: ': ICLRStrongName:: Strongnamesignaturedoğrulamaları Icationex yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0e1692d7151e09a621b93823424b3ac10b6607d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789768"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="bd746-103">ICLRStrongName::StrongNameSignatureVerificationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd746-103">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>

<span data-ttu-id="bd746-104">Belirtilen yoldaki Derleme bildiriminin bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="bd746-104">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd746-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd746-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd746-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd746-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="bd746-107">'ndaki Doğrulanacak derleme için taşınabilir yürütülebilir (. exe veya. dll) dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="bd746-107">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="bd746-108">[in] `true` doğrulama gerçekleştirmek için, kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="bd746-108">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="bd746-109">[out] `true` tanımlayıcı ad imzası doğrulandıysa; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="bd746-109">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="bd746-110">`pfWasVerified` , `false` kayıt defteri ayarları nedeniyle doğrulama başarılı olduysa olarak da ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bd746-110">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd746-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bd746-111">Return Value</span></span>  

 <span data-ttu-id="bd746-112">`S_OK` doğrulama başarılı olduysa, Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="bd746-112">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd746-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd746-113">Remarks</span></span>  

 <span data-ttu-id="bd746-114">[ICLRStrongName:: Strongnamesignaturedoğrulamaları Icationex](iclrstrongname-strongnamesignatureverificationex-method.md) yöntemi [ICLRStrongName:: Strongnamesignaturedoğrulama](iclrstrongname-strongnamesignatureverification-method.md) yöntemine benzer bir yetenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd746-114">The [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="bd746-115">Ancak, ikinci giriş parametresi ve [ICLRStrongName:: Strongnamesignaturedoğrulamaları Icationex](iclrstrongname-strongnamesignatureverificationex-method.md) için çıkış parametresi `BOOLEAN` yerine türüdür `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="bd746-115">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd746-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd746-116">Requirements</span></span>  

 <span data-ttu-id="bd746-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd746-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd746-118">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="bd746-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bd746-119">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="bd746-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd746-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd746-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd746-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd746-121">See also</span></span>

- [<span data-ttu-id="bd746-122">StrongNameSignatureVerification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd746-122">StrongNameSignatureVerification Method</span></span>](iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="bd746-123">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd746-123">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
