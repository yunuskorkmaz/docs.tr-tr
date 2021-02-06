---
description: 'Daha fazla bilgi edinin: Strongnamesignaturedoğrulama Işlevi'
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
ms.openlocfilehash: 74130cda96f38218d2fd296ff8804f86a9a18cd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636274"
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="3d920-103">StrongNameSignatureVerification İşlevi</span><span class="sxs-lookup"><span data-stu-id="3d920-103">StrongNameSignatureVerification Function</span></span>

<span data-ttu-id="3d920-104">Belirtilen bayrağa göre doğrulanan bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="3d920-104">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="3d920-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="3d920-105">This function has been deprecated.</span></span> <span data-ttu-id="3d920-106">Bunun yerine [ICLRStrongName:: Strongnamesignaturedoğrulaması](../hosting/iclrstrongname-strongnamesignatureverification-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="3d920-106">Use the [ICLRStrongName::StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d920-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d920-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d920-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d920-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="3d920-109">'ndaki Doğrulanacak derleme için taşınabilir yürütülebilir (. dll veya. exe) dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="3d920-109">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="3d920-110">'ndaki Doğrulama davranışını değiştirecek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="3d920-110">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="3d920-111">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3d920-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="3d920-112">`SN_INFLAG_FORCE_VER` (0x00000001)-kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="3d920-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="3d920-113">`SN_INFLAG_INSTALL` (0x00000002)-bildirimin doğrulandığı ilk zaman olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d920-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="3d920-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004)-önbelleğin yalnızca yönetici ayrıcalıklarına sahip olan kullanıcılar için erişime izin verolacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d920-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="3d920-115">`SN_INFLAG_USER_ACCESS` (0x00000008)-derlemenin yalnızca geçerli kullanıcı için erişilebilir olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d920-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="3d920-116">`SN_INFLAG_ALL_ACCESS` (0x00000010)-önbelleğin erişim kısıtlaması garantisi sunmayacak olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d920-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="3d920-117">`SN_INFLAG_RUNTIME` (0x80000000)-iç hata ayıklama için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3d920-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="3d920-118">dışı Tanımlayıcı ad imzasının doğrulanıp doğrulanmadığını belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="3d920-118">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="3d920-119">Aşağıdaki değer desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3d920-119">The following value is supported:</span></span>  
  
- <span data-ttu-id="3d920-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-Bu değer `false` , kayıt defteri ayarları nedeniyle doğrulamanın başarılı olduğunu belirtmek için olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3d920-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d920-121">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3d920-121">Return Value</span></span>  

 <span data-ttu-id="3d920-122">`true` doğrulama başarılı olduysa, Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="3d920-122">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d920-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d920-123">Requirements</span></span>  

 <span data-ttu-id="3d920-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d920-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d920-125">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="3d920-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3d920-126">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3d920-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3d920-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d920-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d920-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d920-128">See also</span></span>

- [<span data-ttu-id="3d920-129">StrongNameSignatureVerification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d920-129">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="3d920-130">StrongNameSignatureVerificationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d920-130">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="3d920-131">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d920-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
