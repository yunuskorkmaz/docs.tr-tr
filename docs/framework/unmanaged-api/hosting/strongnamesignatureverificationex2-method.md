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
ms.openlocfilehash: 81640e8e34335898f4dd7f4f43eafbd3ef191d19
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938165"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="b91bc-102">StrongNameSignatureVerificationEx2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b91bc-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="b91bc-103">Kesin adlandırılmış bir derlemenin imzasını doğrular ve ECMA anahtarından gerçek bir anahtara bir eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="b91bc-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b91bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b91bc-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b91bc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b91bc-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b91bc-106">'ndaki Doğrulanacak derleme için taşınabilir yürütülebilir (. exe veya. dll) dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="b91bc-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="b91bc-107">[in] kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulama gerçekleştirmek için `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="b91bc-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="b91bc-108">'ndaki ECMA ortak anahtarından, doğrulama için kullanılan gerçek anahtara eşleme işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b91bc-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="b91bc-109">'ndaki Gerçek ECMA ortak anahtarının uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="b91bc-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="b91bc-110">[out] tanımlayıcı ad imzası doğrulandıysa `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="b91bc-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="b91bc-111">Bu parametre, kayıt defteri ayarları nedeniyle başarılı olduysa de `false` olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b91bc-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b91bc-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b91bc-112">Return Value</span></span>  
 <span data-ttu-id="b91bc-113">doğrulama başarılı olduysa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="b91bc-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b91bc-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b91bc-114">Requirements</span></span>  
 <span data-ttu-id="b91bc-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b91bc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b91bc-116">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="b91bc-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b91bc-117">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="b91bc-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b91bc-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b91bc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b91bc-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b91bc-119">See also</span></span>

- [<span data-ttu-id="b91bc-120">StrongNameSignatureVerification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b91bc-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="b91bc-121">StrongNameSignatureVerificationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b91bc-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="b91bc-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b91bc-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
