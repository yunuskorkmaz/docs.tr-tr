---
description: 'Daha fazla bilgi edinin: StrongNameSignatureGeneration Işlevi'
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
ms.openlocfilehash: 6f5a164e73af743cdd13390c60d00d553e5e0312
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798907"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="ba1fd-103">StrongNameSignatureGeneration İşlevi</span><span class="sxs-lookup"><span data-stu-id="ba1fd-103">StrongNameSignatureGeneration Function</span></span>

<span data-ttu-id="ba1fd-104">Belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-104">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="ba1fd-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-105">This function has been deprecated.</span></span> <span data-ttu-id="ba1fd-106">Bunun yerine [ICLRStrongName:: StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-106">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba1fd-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba1fd-107">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ba1fd-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba1fd-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="ba1fd-109">'ndaki Tanımlayıcı ad imzasının üretilecektir derlemenin bildirimini içeren dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-109">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="ba1fd-110">'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-110">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="ba1fd-111">`pbKeyBlob`Null ise, `wszKeyContainer` şifreleme hizmet sağlayıcısı (CSP) içinde geçerli bir kapsayıcı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-111">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="ba1fd-112">Bu durumda, kapsayıcıda depolanan anahtar çifti dosyayı imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-112">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="ba1fd-113">`pbKeyBlob`Null değilse, anahtar çiftinin anahtar ikili büyük nesne (blob) içinde yer aldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-113">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="ba1fd-114">Anahtarlar 1024-bit Rivest-Shamir-Adtaman (RSA) imzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-114">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="ba1fd-115">Şu anda başka türde anahtarlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-115">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ba1fd-116">'ndaki Ortak/özel anahtar çifti işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-116">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="ba1fd-117">Bu çift Win32 işlevi tarafından oluşturulan biçimdedir `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="ba1fd-117">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="ba1fd-118">`pbKeyBlob`Null ise, tarafından belirtilen anahtar kapsayıcının `wszKeyContainer` anahtar çiftini içermesi varsayılır.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-118">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ba1fd-119">'ndaki Bayt cinsinden boyutu `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="ba1fd-119">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="ba1fd-120">dışı Ortak dil çalışma zamanının imzayı döndürdüğü konuma yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-120">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="ba1fd-121">`ppbSignatureBlob`Null ise, çalışma zamanı imzayı tarafından belirtilen dosyada depolar `wszFilePath` .</span><span class="sxs-lookup"><span data-stu-id="ba1fd-121">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="ba1fd-122">`ppbSignatureBlob`Null değilse, ortak dil çalışma zamanı, imzanın geri döndürüleceği alanı ayırır.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-122">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="ba1fd-123">Çağıranın, [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak bu alanı boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-123">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="ba1fd-124">dışı Döndürülen imzanın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-124">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba1fd-125">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ba1fd-125">Return Value</span></span>  

 <span data-ttu-id="ba1fd-126">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="ba1fd-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba1fd-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba1fd-127">Remarks</span></span>  

 <span data-ttu-id="ba1fd-128">İmza `wszFilePath` boyutunu imzayı oluşturmadan hesaplamak için null değerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="ba1fd-129">İmza, doğrudan dosyada depolanabilir veya çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-129">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="ba1fd-130">`StrongNameSignatureGeneration`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-130">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba1fd-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba1fd-131">Requirements</span></span>  

 <span data-ttu-id="ba1fd-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba1fd-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba1fd-133">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="ba1fd-133">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ba1fd-134">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ba1fd-134">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ba1fd-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba1fd-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba1fd-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba1fd-136">See also</span></span>

- [<span data-ttu-id="ba1fd-137">StrongNameSignatureGeneration Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba1fd-137">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="ba1fd-138">StrongNameSignatureGenerationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba1fd-138">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="ba1fd-139">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba1fd-139">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
