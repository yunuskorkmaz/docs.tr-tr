---
title: StrongNameSignatureGeneration İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
ms.openlocfilehash: d7f481e5c61ec65d2e7414bd47227866f3435028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176909"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="faee9-102">StrongNameSignatureGeneration İşlevi</span><span class="sxs-lookup"><span data-stu-id="faee9-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="faee9-103">Belirtilen derleme için güçlü bir ad imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="faee9-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="faee9-104">Bu işlev amortismana kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="faee9-104">This function has been deprecated.</span></span> <span data-ttu-id="faee9-105">Bunun yerine [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="faee9-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faee9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="faee9-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="faee9-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="faee9-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="faee9-108">[içinde] Güçlü ad imzasının oluşturulacağı derlemenin bildirimini içeren dosyaya giden yol.</span><span class="sxs-lookup"><span data-stu-id="faee9-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="faee9-109">[içinde] Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="faee9-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="faee9-110">Null `pbKeyBlob` ise, `wszKeyContainer` şifreleme hizmet sağlayıcısı (CSP) içinde geçerli bir kapsayıcı belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="faee9-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="faee9-111">Bu durumda, dosyayı imzalamak için kapsayıcıda depolanan anahtar çifti kullanılır.</span><span class="sxs-lookup"><span data-stu-id="faee9-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="faee9-112">Null `pbKeyBlob` değilse, anahtar çiftinin anahtar ikili büyük nesnesinde (BLOB) bulunduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="faee9-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="faee9-113">Anahtarlar 1024 bit Rivest-Shamir-Adleman (RSA) imzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="faee9-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="faee9-114">Şu anda başka anahtar türü desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="faee9-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="faee9-115">[içinde] Ortak/özel anahtar çiftine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="faee9-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="faee9-116">Bu çift Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="faee9-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="faee9-117">Null `pbKeyBlob` ise, tarafından `wszKeyContainer` belirtilen anahtar kapsayıcı anahtar çiftini içerdiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="faee9-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="faee9-118">[içinde] Boyutu, bayt, ve. `pbKeyBlob`</span><span class="sxs-lookup"><span data-stu-id="faee9-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="faee9-119">[çıkış] Ortak dil çalışma zamanının imzayı döndürdettiği konuma işaretçi.</span><span class="sxs-lookup"><span data-stu-id="faee9-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="faee9-120">Null `ppbSignatureBlob` ise, çalışma zamanı tarafından belirtilen dosyada `wszFilePath`imzayı depolar.</span><span class="sxs-lookup"><span data-stu-id="faee9-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="faee9-121">Null `ppbSignatureBlob` değilse, ortak dil çalışma zamanı imzayı döndürmek için alan ayırır.</span><span class="sxs-lookup"><span data-stu-id="faee9-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="faee9-122">Arayan, [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak bu alanı boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="faee9-122">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="faee9-123">[çıkış] Döndürülen imzanın baytlar halindeki boyutu.</span><span class="sxs-lookup"><span data-stu-id="faee9-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="faee9-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="faee9-124">Return Value</span></span>  
 <span data-ttu-id="faee9-125">`true`başarılı bir şekilde tamamlandığında; aksi `false`takdirde, .</span><span class="sxs-lookup"><span data-stu-id="faee9-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="faee9-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="faee9-126">Remarks</span></span>  
 <span data-ttu-id="faee9-127">İmza oluşturmadan imzanın boyutunu hesaplamak için `wszFilePath` null belirtin.</span><span class="sxs-lookup"><span data-stu-id="faee9-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="faee9-128">İmza doğrudan dosyada depolanabilir veya arayana döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="faee9-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="faee9-129">`StrongNameSignatureGeneration` İşlev başarıyla tamamlanmamışsa, oluşturulan son hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini arayın.</span><span class="sxs-lookup"><span data-stu-id="faee9-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faee9-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="faee9-130">Requirements</span></span>  
 <span data-ttu-id="faee9-131">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faee9-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faee9-132">**Üstbilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="faee9-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="faee9-133">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="faee9-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="faee9-134">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faee9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faee9-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faee9-135">See also</span></span>

- [<span data-ttu-id="faee9-136">StrongNameSignatureGeneration Yöntemi</span><span class="sxs-lookup"><span data-stu-id="faee9-136">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="faee9-137">StrongNameSignatureGenerationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="faee9-137">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="faee9-138">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="faee9-138">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
