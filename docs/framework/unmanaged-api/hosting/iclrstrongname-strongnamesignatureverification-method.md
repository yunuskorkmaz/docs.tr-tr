---
description: ': ICLRStrongName:: Strongnamesignaturedoğrulama yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 985a00ffe464f2dd6a92c299dae14206fd37a898
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781850"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="38538-103">ICLRStrongName::StrongNameSignatureVerification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38538-103">ICLRStrongName::StrongNameSignatureVerification Method</span></span>

<span data-ttu-id="38538-104">Belirtilen bayrağa göre doğrulanan bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="38538-104">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38538-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38538-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38538-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38538-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="38538-107">'ndaki Doğrulanacak derleme için taşınabilir yürütülebilir (. dll veya. exe) dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="38538-107">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="38538-108">'ndaki Doğrulama davranışını değiştirecek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="38538-108">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="38538-109">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="38538-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="38538-110">`SN_INFLAG_FORCE_VER` (0x00000001)-kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="38538-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="38538-111">`SN_INFLAG_INSTALL` (0x00000002)-bildirimin doğrulandığı ilk zaman olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="38538-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="38538-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004)-önbelleğin yalnızca yönetici ayrıcalıklarına sahip olan kullanıcılar için erişime izin verolacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="38538-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="38538-113">`SN_INFLAG_USER_ACCESS` (0x00000008)-derlemenin yalnızca geçerli kullanıcı için erişilebilir olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="38538-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="38538-114">`SN_INFLAG_ALL_ACCESS` (0x00000010)-önbelleğin erişim kısıtlaması garantisi sunmayacak olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="38538-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="38538-115">`SN_INFLAG_RUNTIME` (0x80000000)-iç hata ayıklama için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="38538-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="38538-116">dışı Tanımlayıcı ad imzasının doğrulanıp doğrulanmadığını belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="38538-116">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="38538-117">Aşağıdaki değer desteklenir:</span><span class="sxs-lookup"><span data-stu-id="38538-117">The following value is supported:</span></span>  
  
- <span data-ttu-id="38538-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-Bu değer `false` , kayıt defteri ayarları nedeniyle doğrulamanın başarılı olduğunu belirtmek için olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="38538-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38538-119">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="38538-119">Return Value</span></span>  

 <span data-ttu-id="38538-120">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="38538-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38538-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38538-121">Requirements</span></span>  

 <span data-ttu-id="38538-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38538-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38538-123">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="38538-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="38538-124">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="38538-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38538-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38538-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38538-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38538-126">See also</span></span>

- [<span data-ttu-id="38538-127">StrongNameSignatureVerificationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38538-127">StrongNameSignatureVerificationEx Method</span></span>](iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="38538-128">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38538-128">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
