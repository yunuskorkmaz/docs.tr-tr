---
title: StrongNameSignatureVerification İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8943df861b1bff2b28c68d0233fc336d1b5d4579
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798940"
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="cb7ab-102">StrongNameSignatureVerification İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb7ab-102">StrongNameSignatureVerification Function</span></span>
<span data-ttu-id="cb7ab-103">Belirtilen bayrağa göre doğrulanan bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="cb7ab-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="cb7ab-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="cb7ab-104">This function has been deprecated.</span></span> <span data-ttu-id="cb7ab-105">Bunun yerine [ICLRStrongName:: Strongnamesignaturedoğrulaması](../hosting/iclrstrongname-strongnamesignatureverification-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="cb7ab-105">Use the [ICLRStrongName::StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb7ab-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb7ab-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb7ab-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb7ab-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="cb7ab-108">'ndaki Doğrulanacak derleme için taşınabilir yürütülebilir (. dll veya. exe) dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="cb7ab-108">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="cb7ab-109">'ndaki Doğrulama davranışını değiştirecek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="cb7ab-109">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="cb7ab-110">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="cb7ab-110">The following values are supported:</span></span>  
  
- <span data-ttu-id="cb7ab-111">`SN_INFLAG_FORCE_VER`(0x00000001)-kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="cb7ab-111">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="cb7ab-112">`SN_INFLAG_INSTALL`(0x00000002)-bildirimin doğrulandığı ilk zaman olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb7ab-112">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="cb7ab-113">`SN_INFLAG_ADMIN_ACCESS`(0x00000004)-önbelleğin yalnızca yönetici ayrıcalıklarına sahip olan kullanıcılar için erişime izin verolacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb7ab-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="cb7ab-114">`SN_INFLAG_USER_ACCESS`(0x00000008)-derlemenin yalnızca geçerli kullanıcı için erişilebilir olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb7ab-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="cb7ab-115">`SN_INFLAG_ALL_ACCESS`(0x00000010)-önbelleğin erişim kısıtlaması garantisi sunmayacak olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb7ab-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="cb7ab-116">`SN_INFLAG_RUNTIME`(0x80000000)-iç hata ayıklama için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="cb7ab-116">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="cb7ab-117">dışı Tanımlayıcı ad imzasının doğrulanıp doğrulanmadığını belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="cb7ab-117">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="cb7ab-118">Aşağıdaki değer desteklenir:</span><span class="sxs-lookup"><span data-stu-id="cb7ab-118">The following value is supported:</span></span>  
  
- <span data-ttu-id="cb7ab-119">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001)-Bu değer, kayıt defteri `false` ayarları nedeniyle doğrulamanın başarılı olduğunu belirtmek için olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cb7ab-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb7ab-120">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cb7ab-120">Return Value</span></span>  
 <span data-ttu-id="cb7ab-121">`true`doğrulama başarılı olduysa, Aksi takdirde `false`,.</span><span class="sxs-lookup"><span data-stu-id="cb7ab-121">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb7ab-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb7ab-122">Requirements</span></span>  
 <span data-ttu-id="cb7ab-123">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb7ab-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb7ab-124">**Üst bilgi** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="cb7ab-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cb7ab-125">**Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="cb7ab-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb7ab-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb7ab-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb7ab-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb7ab-127">See also</span></span>

- [<span data-ttu-id="cb7ab-128">StrongNameSignatureVerification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb7ab-128">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="cb7ab-129">StrongNameSignatureVerificationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb7ab-129">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="cb7ab-130">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb7ab-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
