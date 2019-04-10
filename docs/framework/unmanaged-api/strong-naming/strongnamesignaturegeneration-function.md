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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e7df65c28fad6fa79ec7a18d8511955330b2817
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227749"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="bac43-102">StrongNameSignatureGeneration İşlevi</span><span class="sxs-lookup"><span data-stu-id="bac43-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="bac43-103">Tanımlayıcı ad imzası için belirtilen derlemeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bac43-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="bac43-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="bac43-104">This function has been deprecated.</span></span> <span data-ttu-id="bac43-105">Kullanım [Iclrstrongname::strongnamesignaturegeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="bac43-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bac43-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bac43-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bac43-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bac43-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="bac43-108">[in] Tanımlayıcı ad imzası oluşturulacak derleme bildirimi içeren dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="bac43-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="bac43-109">[in] Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="bac43-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="bac43-110">Varsa `pbKeyBlob` boş `wszKeyContainer` şifreleme hizmeti sağlayıcısı (CSP) geçerli bir kapsayıcıda belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bac43-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="bac43-111">Bu durumda, bir kapsayıcıda depolanan bir anahtar çifti dosyasını imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bac43-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="bac43-112">Varsa `pbKeyBlob` anahtar çiftini varsayılır anahtar ikili büyük nesne içinde (BLOB) dahil edilmek üzere null değil.</span><span class="sxs-lookup"><span data-stu-id="bac43-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="bac43-113">Anahtarları 1024 bit Rivest-Shamir-Adleman (RSA) imzalama anahtarı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bac43-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="bac43-114">Anahtarlar başka tür bu zaman desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bac43-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="bac43-115">[in] Ortak/özel anahtar çifti için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bac43-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="bac43-116">Win32 oluşturulan biçimde bu çiftidir `CryptExportKey` işlevi.</span><span class="sxs-lookup"><span data-stu-id="bac43-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="bac43-117">Varsa `pbKeyBlob` null, belirtilen anahtar kapsayıcısı olan `wszKeyContainer` anahtar çiftini içerdiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="bac43-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="bac43-118">[in] Bayt cinsinden boyutu, `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="bac43-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="bac43-119">[out] Ortak dil çalışma zamanı imza döndüren konumu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bac43-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="bac43-120">Varsa `ppbSignatureBlob` olduğundan çalışma zamanı tarafından belirtilen dosyada imza null depolar `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="bac43-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="bac43-121">Varsa `ppbSignatureBlob` olan null, ortak dil çalışma zamanı imza döndürmek alan ayırır.</span><span class="sxs-lookup"><span data-stu-id="bac43-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="bac43-122">Çağıranın kullanarak bu alan boşaltmanız gerekir [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="bac43-122">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="bac43-123">[out] Baytlarında döndürülen imza boyutu.</span><span class="sxs-lookup"><span data-stu-id="bac43-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bac43-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bac43-124">Return Value</span></span>  
 `true` <span data-ttu-id="bac43-125">başarıyla tamamlandığında; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="bac43-125">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bac43-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bac43-126">Remarks</span></span>  
 <span data-ttu-id="bac43-127">İçin null belirtin `wszFilePath` imza oluşturmadan imza boyutunu hesaplamak için.</span><span class="sxs-lookup"><span data-stu-id="bac43-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="bac43-128">İmza olabilir ya da doğrudan dosyasında depolanan veya arayana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="bac43-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="bac43-129">Varsa `StrongNameSignatureGeneration` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.</span><span class="sxs-lookup"><span data-stu-id="bac43-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bac43-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bac43-130">Requirements</span></span>  
 <span data-ttu-id="bac43-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bac43-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bac43-132">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="bac43-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="bac43-133">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bac43-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="bac43-134">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="bac43-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bac43-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bac43-135">See also</span></span>

- [<span data-ttu-id="bac43-136">StrongNameSignatureGeneration Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bac43-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="bac43-137">StrongNameSignatureGenerationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bac43-137">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="bac43-138">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bac43-138">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
