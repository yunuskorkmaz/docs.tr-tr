---
title: ICLRStrongName::StrongNameSignatureGenerationEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b411a51a5640a924d3eeae5d52102a842966d3fa
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855503"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="919e1-102">ICLRStrongName::StrongNameSignatureGenerationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="919e1-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="919e1-103">Belirtilen bayrağa göre belirtilen derleme için bir tanımlayıcı ad imzası üretir.</span><span class="sxs-lookup"><span data-stu-id="919e1-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="919e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="919e1-104">Syntax</span></span>  
  
```cpp
HRESULT StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="919e1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="919e1-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="919e1-106">'ndaki Tanımlayıcı ad imzasının üretilecektir derlemenin bildirimini içeren dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="919e1-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="919e1-107">'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="919e1-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="919e1-108">Null ise, `wszKeyContainer` şifreleme hizmet sağlayıcısı (CSP) içinde geçerli bir kapsayıcı belirtmeniz gerekir. `pbKeyBlob`</span><span class="sxs-lookup"><span data-stu-id="919e1-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="919e1-109">Bu durumda, kapsayıcıda depolanan anahtar çifti dosyayı imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="919e1-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="919e1-110">`pbKeyBlob` Null değilse, anahtar çiftinin anahtar ikili büyük nesne (blob) içinde yer aldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="919e1-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="919e1-111">'ndaki Ortak/özel anahtar çifti işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="919e1-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="919e1-112">Bu çift Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="919e1-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="919e1-113">Null ise, tarafından `wszKeyContainer` belirtilen anahtar kapsayıcının anahtar çiftini içermesi varsayılır. `pbKeyBlob`</span><span class="sxs-lookup"><span data-stu-id="919e1-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="919e1-114">'ndaki Bayt cinsinden boyutu `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="919e1-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="919e1-115">dışı Ortak dil çalışma zamanının imzayı döndürdüğü konuma yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="919e1-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="919e1-116">Null ise, çalışma zamanı imzayı tarafından `wszFilePath`belirtilen dosyada depolar. `ppbSignatureBlob`</span><span class="sxs-lookup"><span data-stu-id="919e1-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="919e1-117">`ppbSignatureBlob` Null değilse, ortak dil çalışma zamanı, imzanın geri döndürüleceği alanı ayırır.</span><span class="sxs-lookup"><span data-stu-id="919e1-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="919e1-118">Çağıranın [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodunu kullanarak bu alanı boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="919e1-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="919e1-119">dışı Döndürülen imzanın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="919e1-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="919e1-120">'ndaki Aşağıdaki değerlerden biri veya daha fazlası:</span><span class="sxs-lookup"><span data-stu-id="919e1-120">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="919e1-121">`SN_SIGN_ALL_FILES`(0x00000001)-bağlantılı modüller için tüm karmaların yeniden hesaplanması.</span><span class="sxs-lookup"><span data-stu-id="919e1-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="919e1-122">`SN_TEST_SIGN`(0x00000002)-derlemeyi test-imzala.</span><span class="sxs-lookup"><span data-stu-id="919e1-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="919e1-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="919e1-123">Return Value</span></span>  
 <span data-ttu-id="919e1-124">`S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](https://go.microsoft.com/fwlink/?LinkId=213878) ).</span><span class="sxs-lookup"><span data-stu-id="919e1-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="919e1-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="919e1-125">Remarks</span></span>  
 <span data-ttu-id="919e1-126">İmza boyutunu imzayı `wszFilePath` oluşturmadan hesaplamak için null değerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="919e1-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="919e1-127">İmza doğrudan dosyada depolanabilir veya çağırana geri döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="919e1-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="919e1-128">Belirtilirse, ancak bir ortak anahtar dahil edilmez ( `wszFilePath` hem hem de `pbKeyBlob` null ise), bağlantılı modüllerin karmaları yeniden hesaplanır, ancak derleme yeniden imzalanmamıştır. `SN_SIGN_ALL_FILES`</span><span class="sxs-lookup"><span data-stu-id="919e1-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="919e1-129">`SN_TEST_SIGN` Belirtilmişse, derlemenin tanımlayıcı bir adla imzalandığını göstermek için ortak dil çalışma zamanı üst bilgisi değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="919e1-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="919e1-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="919e1-130">Requirements</span></span>  
 <span data-ttu-id="919e1-131">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="919e1-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="919e1-132">**Üst bilgi** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="919e1-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="919e1-133">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="919e1-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="919e1-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="919e1-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="919e1-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="919e1-135">See also</span></span>

- [<span data-ttu-id="919e1-136">StrongNameSignatureGeneration Yöntemi</span><span class="sxs-lookup"><span data-stu-id="919e1-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="919e1-137">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="919e1-137">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
