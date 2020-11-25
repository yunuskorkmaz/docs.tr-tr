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
ms.openlocfilehash: 78a89c07b9a7ddbccee9716de37c96d23635f87b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708536"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="5340c-102">StrongNameSignatureGeneration İşlevi</span><span class="sxs-lookup"><span data-stu-id="5340c-102">StrongNameSignatureGeneration Function</span></span>

<span data-ttu-id="5340c-103">Belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5340c-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="5340c-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="5340c-104">This function has been deprecated.</span></span> <span data-ttu-id="5340c-105">Bunun yerine [ICLRStrongName:: StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="5340c-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5340c-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5340c-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5340c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5340c-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="5340c-108">'ndaki Tanımlayıcı ad imzasının üretilecektir derlemenin bildirimini içeren dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="5340c-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="5340c-109">'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="5340c-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="5340c-110">`pbKeyBlob`Null ise, `wszKeyContainer` şifreleme hizmet sağlayıcısı (CSP) içinde geçerli bir kapsayıcı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5340c-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="5340c-111">Bu durumda, kapsayıcıda depolanan anahtar çifti dosyayı imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5340c-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="5340c-112">`pbKeyBlob`Null değilse, anahtar çiftinin anahtar ikili büyük nesne (blob) içinde yer aldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="5340c-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="5340c-113">Anahtarlar 1024-bit Rivest-Shamir-Adtaman (RSA) imzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5340c-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="5340c-114">Şu anda başka türde anahtarlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="5340c-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="5340c-115">'ndaki Ortak/özel anahtar çifti işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5340c-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="5340c-116">Bu çift Win32 işlevi tarafından oluşturulan biçimdedir `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="5340c-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="5340c-117">`pbKeyBlob`Null ise, tarafından belirtilen anahtar kapsayıcının `wszKeyContainer` anahtar çiftini içermesi varsayılır.</span><span class="sxs-lookup"><span data-stu-id="5340c-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="5340c-118">'ndaki Bayt cinsinden boyutu `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="5340c-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="5340c-119">dışı Ortak dil çalışma zamanının imzayı döndürdüğü konuma yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5340c-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="5340c-120">`ppbSignatureBlob`Null ise, çalışma zamanı imzayı tarafından belirtilen dosyada depolar `wszFilePath` .</span><span class="sxs-lookup"><span data-stu-id="5340c-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="5340c-121">`ppbSignatureBlob`Null değilse, ortak dil çalışma zamanı, imzanın geri döndürüleceği alanı ayırır.</span><span class="sxs-lookup"><span data-stu-id="5340c-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="5340c-122">Çağıranın, [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak bu alanı boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5340c-122">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="5340c-123">dışı Döndürülen imzanın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="5340c-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5340c-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5340c-124">Return Value</span></span>  

 <span data-ttu-id="5340c-125">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="5340c-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5340c-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5340c-126">Remarks</span></span>  

 <span data-ttu-id="5340c-127">İmza `wszFilePath` boyutunu imzayı oluşturmadan hesaplamak için null değerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="5340c-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="5340c-128">İmza, doğrudan dosyada depolanabilir veya çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5340c-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="5340c-129">`StrongNameSignatureGeneration`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="5340c-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5340c-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5340c-130">Requirements</span></span>  

 <span data-ttu-id="5340c-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5340c-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5340c-132">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="5340c-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="5340c-133">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5340c-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5340c-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5340c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5340c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5340c-135">See also</span></span>

- [<span data-ttu-id="5340c-136">StrongNameSignatureGeneration Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5340c-136">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="5340c-137">StrongNameSignatureGenerationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5340c-137">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="5340c-138">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5340c-138">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
