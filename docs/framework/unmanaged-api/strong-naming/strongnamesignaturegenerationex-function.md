---
title: StrongNameSignatureGenerationEx İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGenerationEx
helpviewer_keywords:
- StrongNameSignatureGenerationEx function [.NET Framework strong naming]
ms.assetid: 9a75469e-aa49-4e32-ad48-3bafd5202f09
topic_type:
- apiref
ms.openlocfilehash: 96dae519d73505a30c8593e9883da7338525ea2c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708529"
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="8c182-102">StrongNameSignatureGenerationEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="8c182-102">StrongNameSignatureGenerationEx Function</span></span>

<span data-ttu-id="8c182-103">Belirtilen bayrağa göre belirtilen derleme için bir tanımlayıcı ad imzası üretir.</span><span class="sxs-lookup"><span data-stu-id="8c182-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="8c182-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="8c182-104">This function has been deprecated.</span></span> <span data-ttu-id="8c182-105">Bunun yerine [ICLRStrongName:: StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="8c182-105">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c182-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8c182-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c182-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8c182-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="8c182-108">'ndaki Tanımlayıcı ad imzasının üretilecektir derlemenin bildirimini içeren dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="8c182-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="8c182-109">'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="8c182-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="8c182-110">`pbKeyBlob`Null ise, `wszKeyContainer` şifreleme hizmet sağlayıcısı (CSP) içinde geçerli bir kapsayıcı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c182-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="8c182-111">Bu durumda, kapsayıcıda depolanan anahtar çifti dosyayı imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c182-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="8c182-112">`pbKeyBlob`Null değilse, anahtar çiftinin anahtar ikili büyük nesne (blob) içinde yer aldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="8c182-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="8c182-113">'ndaki Ortak/özel anahtar çifti işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8c182-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="8c182-114">Bu çift Win32 işlevi tarafından oluşturulan biçimdedir `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="8c182-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="8c182-115">`pbKeyBlob`Null ise, tarafından belirtilen anahtar kapsayıcının `wszKeyContainer` anahtar çiftini içermesi varsayılır.</span><span class="sxs-lookup"><span data-stu-id="8c182-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="8c182-116">'ndaki Bayt cinsinden boyutu `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="8c182-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="8c182-117">dışı Ortak dil çalışma zamanının imzayı döndürdüğü konuma yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8c182-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="8c182-118">`ppbSignatureBlob`Null ise, çalışma zamanı imzayı tarafından belirtilen dosyada depolar `wszFilePath` .</span><span class="sxs-lookup"><span data-stu-id="8c182-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="8c182-119">`ppbSignatureBlob`Null değilse, ortak dil çalışma zamanı, imzanın geri döndürüleceği alanı ayırır.</span><span class="sxs-lookup"><span data-stu-id="8c182-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="8c182-120">Çağıranın, [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak bu alanı boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8c182-120">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="8c182-121">dışı Döndürülen imzanın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="8c182-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8c182-122">'ndaki Aşağıdaki değerlerden biri veya daha fazlası:</span><span class="sxs-lookup"><span data-stu-id="8c182-122">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="8c182-123">`SN_SIGN_ALL_FILES` (0x00000001)-bağlantılı modüller için tüm karmaların yeniden hesaplanması.</span><span class="sxs-lookup"><span data-stu-id="8c182-123">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="8c182-124">`SN_TEST_SIGN` (0x00000002)-derlemeyi test-imzala.</span><span class="sxs-lookup"><span data-stu-id="8c182-124">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c182-125">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8c182-125">Return Value</span></span>  

 <span data-ttu-id="8c182-126">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="8c182-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c182-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c182-127">Remarks</span></span>  

 <span data-ttu-id="8c182-128">İmza `wszFilePath` boyutunu imzayı oluşturmadan hesaplamak için null değerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="8c182-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="8c182-129">İmza doğrudan dosyada depolanabilir veya çağırana geri döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="8c182-129">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="8c182-130">`SN_SIGN_ALL_FILES`Belirtilirse, ancak bir ortak anahtar dahil edilmez (hem hem de `pbKeyBlob` null ise `wszFilePath` ), bağlantılı modüllerin karmaları yeniden hesaplanır, ancak derleme yeniden imzalanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="8c182-130">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="8c182-131">`SN_TEST_SIGN`Belirtilmişse, derlemenin tanımlayıcı bir adla imzalandığını göstermek için ortak dil çalışma zamanı üst bilgisi değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="8c182-131">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="8c182-132">`StrongNameSignatureGenerationEx`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="8c182-132">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c182-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c182-133">Requirements</span></span>  

 <span data-ttu-id="8c182-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c182-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c182-135">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="8c182-135">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="8c182-136">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8c182-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c182-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c182-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c182-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c182-138">See also</span></span>

- [<span data-ttu-id="8c182-139">StrongNameSignatureGenerationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8c182-139">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="8c182-140">StrongNameSignatureGeneration Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8c182-140">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="8c182-141">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c182-141">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
