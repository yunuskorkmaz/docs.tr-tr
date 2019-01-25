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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 703b2e90aebd61467063b9ac2d8068c1379e645b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523577"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="f72c2-102">ICLRStrongName::StrongNameSignatureGeneration Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f72c2-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="f72c2-103">Tanımlayıcı ad imzası için belirtilen derlemeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f72c2-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f72c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f72c2-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f72c2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f72c2-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="f72c2-106">[in] Tanımlayıcı ad imzası oluşturulacak derleme bildirimi içeren dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="f72c2-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="f72c2-107">[in] Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="f72c2-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="f72c2-108">Varsa `pbKeyBlob` boş `wszKeyContainer` şifreleme hizmeti sağlayıcısı (CSP) geçerli bir kapsayıcıda belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f72c2-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="f72c2-109">Bu durumda, bir kapsayıcıda depolanan bir anahtar çifti dosyasını imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f72c2-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="f72c2-110">Varsa `pbKeyBlob` anahtar çiftini varsayılır anahtar ikili büyük nesne içinde (BLOB) dahil edilmek üzere null değil.</span><span class="sxs-lookup"><span data-stu-id="f72c2-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="f72c2-111">Anahtarları 1024 bit Rivest-Shamir-Adleman (RSA) imzalama anahtarı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f72c2-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="f72c2-112">Anahtarlar başka tür bu zaman desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f72c2-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="f72c2-113">[in] Ortak/özel anahtar çifti için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f72c2-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="f72c2-114">Win32 oluşturulan biçimde bu çiftidir `CryptExportKey` işlevi.</span><span class="sxs-lookup"><span data-stu-id="f72c2-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="f72c2-115">Varsa `pbKeyBlob` null, belirtilen anahtar kapsayıcısı olan `wszKeyContainer` anahtar çiftini içerdiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="f72c2-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="f72c2-116">[in] Bayt cinsinden boyutu, `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="f72c2-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="f72c2-117">[out] Ortak dil çalışma zamanı imza döndüren konumu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f72c2-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="f72c2-118">Varsa `ppbSignatureBlob` olduğundan çalışma zamanı tarafından belirtilen dosyada imza null depolar `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="f72c2-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="f72c2-119">Varsa `ppbSignatureBlob` olan null, ortak dil çalışma zamanı imza döndürmek alan ayırır.</span><span class="sxs-lookup"><span data-stu-id="f72c2-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="f72c2-120">Çağıranın bu kullanarak boş alan gerekir [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f72c2-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="f72c2-121">[out] Baytlarında döndürülen imza boyutu.</span><span class="sxs-lookup"><span data-stu-id="f72c2-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f72c2-122">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f72c2-122">Return Value</span></span>  
 <span data-ttu-id="f72c2-123">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="f72c2-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f72c2-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f72c2-124">Remarks</span></span>  
 <span data-ttu-id="f72c2-125">İçin null belirtin `wszFilePath` imza oluşturmadan imza boyutunu hesaplamak için.</span><span class="sxs-lookup"><span data-stu-id="f72c2-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="f72c2-126">İmza olabilir ya da doğrudan dosyasında depolanan veya arayana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f72c2-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f72c2-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f72c2-127">Requirements</span></span>  
 <span data-ttu-id="f72c2-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f72c2-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f72c2-129">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f72c2-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f72c2-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f72c2-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f72c2-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f72c2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f72c2-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f72c2-132">See also</span></span>
- [<span data-ttu-id="f72c2-133">StrongNameSignatureGenerationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f72c2-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="f72c2-134">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f72c2-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
