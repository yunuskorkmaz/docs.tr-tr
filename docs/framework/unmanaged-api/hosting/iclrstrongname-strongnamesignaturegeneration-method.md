---
title: ICLRStrongName::StrongNameSignatureGeneration Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
ms.openlocfilehash: a8c9eab719f6a4f233490e544f67cf779ea10b20
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763050"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="b089c-102">ICLRStrongName::StrongNameSignatureGeneration Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b089c-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="b089c-103">Belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b089c-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b089c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b089c-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b089c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b089c-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b089c-106">'ndaki Tanımlayıcı ad imzasının üretilecektir derlemenin bildirimini içeren dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="b089c-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="b089c-107">'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="b089c-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="b089c-108">`pbKeyBlob`Null ise, `wszKeyContainer` şifreleme hizmet sağlayıcısı (CSP) içinde geçerli bir kapsayıcı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b089c-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="b089c-109">Bu durumda, kapsayıcıda depolanan anahtar çifti dosyayı imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b089c-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="b089c-110">`pbKeyBlob`Null değilse, anahtar çiftinin anahtar ikili büyük nesne (blob) içinde yer aldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="b089c-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="b089c-111">Anahtarlar 1024-bit Rivest-Shamir-Adtaman (RSA) imzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b089c-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="b089c-112">Şu anda başka türde anahtarlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="b089c-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="b089c-113">'ndaki Ortak/özel anahtar çifti işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b089c-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="b089c-114">Bu çift Win32 işlevi tarafından oluşturulan biçimdedir `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="b089c-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="b089c-115">`pbKeyBlob`Null ise, tarafından belirtilen anahtar kapsayıcının `wszKeyContainer` anahtar çiftini içermesi varsayılır.</span><span class="sxs-lookup"><span data-stu-id="b089c-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="b089c-116">'ndaki Bayt cinsinden boyutu `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="b089c-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="b089c-117">dışı Ortak dil çalışma zamanının imzayı döndürdüğü konuma yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b089c-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="b089c-118">`ppbSignatureBlob`Null ise, çalışma zamanı imzayı tarafından belirtilen dosyada depolar `wszFilePath` .</span><span class="sxs-lookup"><span data-stu-id="b089c-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="b089c-119">`ppbSignatureBlob`Null değilse, ortak dil çalışma zamanı, imzanın geri döndürüleceği alanı ayırır.</span><span class="sxs-lookup"><span data-stu-id="b089c-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="b089c-120">Çağıran, [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) metodunu kullanarak bu alanı boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b089c-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="b089c-121">dışı Döndürülen imzanın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b089c-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b089c-122">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b089c-122">Return Value</span></span>  
 <span data-ttu-id="b089c-123">`S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="b089c-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b089c-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b089c-124">Remarks</span></span>  
 <span data-ttu-id="b089c-125">İmza `wszFilePath` boyutunu imzayı oluşturmadan hesaplamak için null değerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="b089c-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="b089c-126">İmza, doğrudan dosyada depolanabilir veya çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b089c-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b089c-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b089c-127">Requirements</span></span>  
 <span data-ttu-id="b089c-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b089c-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b089c-129">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="b089c-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b089c-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="b089c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b089c-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b089c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b089c-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b089c-132">See also</span></span>

- [<span data-ttu-id="b089c-133">StrongNameSignatureGenerationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b089c-133">StrongNameSignatureGenerationEx Method</span></span>](iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="b089c-134">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b089c-134">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
