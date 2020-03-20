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
ms.openlocfilehash: e58ac181c4e472c469076b880ff71e0c6afa30fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178047"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="63f99-102">ICLRStrongName::StrongNameSignatureGeneration Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63f99-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="63f99-103">Belirtilen derleme için güçlü bir ad imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="63f99-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63f99-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63f99-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="63f99-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63f99-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="63f99-106">[içinde] Güçlü ad imzasının oluşturulacağı derlemenin bildirimini içeren dosyaya giden yol.</span><span class="sxs-lookup"><span data-stu-id="63f99-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="63f99-107">[içinde] Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="63f99-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="63f99-108">Null `pbKeyBlob` ise, `wszKeyContainer` şifreleme hizmet sağlayıcısı (CSP) içinde geçerli bir kapsayıcı belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="63f99-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="63f99-109">Bu durumda, dosyayı imzalamak için kapsayıcıda depolanan anahtar çifti kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63f99-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="63f99-110">Null `pbKeyBlob` değilse, anahtar çiftinin anahtar ikili büyük nesnesinde (BLOB) bulunduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="63f99-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="63f99-111">Anahtarlar 1024 bit Rivest-Shamir-Adleman (RSA) imzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="63f99-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="63f99-112">Şu anda başka anahtar türü desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="63f99-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="63f99-113">[içinde] Ortak/özel anahtar çiftine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="63f99-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="63f99-114">Bu çift Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="63f99-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="63f99-115">Null `pbKeyBlob` ise, tarafından `wszKeyContainer` belirtilen anahtar kapsayıcı anahtar çiftini içerdiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="63f99-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="63f99-116">[içinde] Boyutu, bayt, ve. `pbKeyBlob`</span><span class="sxs-lookup"><span data-stu-id="63f99-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="63f99-117">[çıkış] Ortak dil çalışma zamanının imzayı döndürdettiği konuma işaretçi.</span><span class="sxs-lookup"><span data-stu-id="63f99-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="63f99-118">Null `ppbSignatureBlob` ise, çalışma zamanı tarafından belirtilen dosyada `wszFilePath`imzayı depolar.</span><span class="sxs-lookup"><span data-stu-id="63f99-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="63f99-119">Null `ppbSignatureBlob` değilse, ortak dil çalışma zamanı imzayı döndürmek için alan ayırır.</span><span class="sxs-lookup"><span data-stu-id="63f99-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="63f99-120">Arayan ICLRStrongName kullanarak bu alanı boşaltmak [gerekir::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="63f99-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="63f99-121">[çıkış] Döndürülen imzanın baytlar halindeki boyutu.</span><span class="sxs-lookup"><span data-stu-id="63f99-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63f99-122">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="63f99-122">Return Value</span></span>  
 <span data-ttu-id="63f99-123">`S_OK`yöntem başarıyla tamamlanırsa; aksi takdirde, başarısızlığı gösteren bir HRESULT değeri (liste için [Ortak HRESULT Değerleri'ne](/windows/win32/seccrypto/common-hresult-values) bakın).</span><span class="sxs-lookup"><span data-stu-id="63f99-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63f99-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63f99-124">Remarks</span></span>  
 <span data-ttu-id="63f99-125">İmza oluşturmadan imzanın boyutunu hesaplamak için `wszFilePath` null belirtin.</span><span class="sxs-lookup"><span data-stu-id="63f99-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="63f99-126">İmza doğrudan dosyada depolanabilir veya arayana döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="63f99-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63f99-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63f99-127">Requirements</span></span>  
 <span data-ttu-id="63f99-128">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63f99-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63f99-129">**Üstbilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="63f99-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="63f99-130">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="63f99-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63f99-131">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63f99-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63f99-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63f99-132">See also</span></span>

- [<span data-ttu-id="63f99-133">StrongNameSignatureGenerationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63f99-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="63f99-134">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63f99-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
