---
title: ICLRStrongName::StrongNameSignatureVerification Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
ms.openlocfilehash: 6375fd8e4a314403267a4cdf2e8356677e9e7a06
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899484"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="e30f2-102">ICLRStrongName::StrongNameSignatureVerification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e30f2-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>
<span data-ttu-id="e30f2-103">Belirtilen bayrağa göre doğrulanan bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="e30f2-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e30f2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e30f2-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e30f2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e30f2-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="e30f2-106">'ndaki Doğrulanacak derleme için taşınabilir yürütülebilir (. dll veya. exe) dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="e30f2-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="e30f2-107">'ndaki Doğrulama davranışını değiştirecek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="e30f2-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="e30f2-108">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="e30f2-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="e30f2-109">`SN_INFLAG_FORCE_VER` (0x00000001)-kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="e30f2-109">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="e30f2-110">`SN_INFLAG_INSTALL` (0x00000002)-bildirimin doğrulandığı ilk zaman olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e30f2-110">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="e30f2-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004)-önbelleğin yalnızca yönetici ayrıcalıklarına sahip olan kullanıcılar için erişime izin verolacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e30f2-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="e30f2-112">`SN_INFLAG_USER_ACCESS` (0x00000008)-derlemenin yalnızca geçerli kullanıcı için erişilebilir olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e30f2-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="e30f2-113">`SN_INFLAG_ALL_ACCESS` (0x00000010)-önbelleğin erişim kısıtlaması garantisi sunmayacak olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e30f2-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="e30f2-114">`SN_INFLAG_RUNTIME` (0x80000000)-iç hata ayıklama için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e30f2-114">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="e30f2-115">dışı Tanımlayıcı ad imzasının doğrulanıp doğrulanmadığını belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="e30f2-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="e30f2-116">Aşağıdaki değer desteklenir:</span><span class="sxs-lookup"><span data-stu-id="e30f2-116">The following value is supported:</span></span>  
  
- <span data-ttu-id="e30f2-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-Bu değer, kayıt defteri ayarları nedeniyle doğrulamanın başarılı olduğunu belirtmek için `false` olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e30f2-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e30f2-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e30f2-118">Return Value</span></span>  
 <span data-ttu-id="e30f2-119">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="e30f2-119">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e30f2-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e30f2-120">Requirements</span></span>  
 <span data-ttu-id="e30f2-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e30f2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e30f2-122">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="e30f2-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e30f2-123">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="e30f2-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e30f2-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e30f2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e30f2-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e30f2-125">See also</span></span>

- [<span data-ttu-id="e30f2-126">StrongNameSignatureVerificationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e30f2-126">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="e30f2-127">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e30f2-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
