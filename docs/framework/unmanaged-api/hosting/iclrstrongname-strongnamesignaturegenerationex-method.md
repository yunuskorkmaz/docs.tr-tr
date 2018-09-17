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
ms.openlocfilehash: 81f1eb4236bab72caf4421342e1f54d6d2f32607
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743905"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="8fa0c-102">ICLRStrongName::StrongNameSignatureGenerationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fa0c-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="8fa0c-103">Belirtilen bayraklar göre belirtilen derleme için tanımlayıcı ad imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fa0c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8fa0c-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="8fa0c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8fa0c-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="8fa0c-106">[in] Tanımlayıcı ad imzası oluşturulacak derleme bildirimi içeren dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="8fa0c-107">[in] Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="8fa0c-108">Varsa `pbKeyBlob` boş `wszKeyContainer` şifreleme hizmeti sağlayıcısı (CSP) geçerli bir kapsayıcıda belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="8fa0c-109">Bu durumda, bir kapsayıcıda depolanan bir anahtar çifti dosyasını imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="8fa0c-110">Varsa `pbKeyBlob` anahtar çiftini varsayılır anahtar ikili büyük nesne içinde (BLOB) dahil edilmek üzere null değil.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="8fa0c-111">[in] Ortak/özel anahtar çifti için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="8fa0c-112">Win32 oluşturulan biçimde bu çiftidir `CryptExportKey` işlevi.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="8fa0c-113">Varsa `pbKeyBlob` null, belirtilen anahtar kapsayıcısı olan `wszKeyContainer` anahtar çiftini içerdiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="8fa0c-114">[in] Bayt cinsinden boyutu, `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="8fa0c-115">[out] Ortak dil çalışma zamanı imza döndüren konumu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="8fa0c-116">Varsa `ppbSignatureBlob` olduğundan çalışma zamanı tarafından belirtilen dosyada imza null depolar `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="8fa0c-117">Varsa `ppbSignatureBlob` olan null, ortak dil çalışma zamanı imza döndürmek alan ayırır.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="8fa0c-118">Çağıranın kullanarak bu alan boşaltmanız gerekir [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="8fa0c-119">[out] Baytlarında döndürülen imza boyutu.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8fa0c-120">[in] Bir veya daha fazla aşağıdaki değerlerden biri:</span><span class="sxs-lookup"><span data-stu-id="8fa0c-120">[in] One or more of the following values:</span></span>  
  
-   <span data-ttu-id="8fa0c-121">`SN_SIGN_ALL_FILES` (0x00000001) - bağlı olan modüller için tüm karmaları yeniden oynatmanız.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
-   <span data-ttu-id="8fa0c-122">`SN_TEST_SIGN` (0x00000002) - derlemeyi test imzalayın.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8fa0c-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8fa0c-123">Return Value</span></span>  
 <span data-ttu-id="8fa0c-124">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="8fa0c-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fa0c-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fa0c-125">Remarks</span></span>  
 <span data-ttu-id="8fa0c-126">İçin null belirtin `wszFilePath` imza oluşturmadan imza boyutunu hesaplamak için.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="8fa0c-127">İmza ya da doğrudan dosyasında depolanan veya arayana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="8fa0c-128">Varsa `SN_SIGN_ALL_FILES` belirtildi ancak ortak anahtar dahil değildir (her ikisi de `pbKeyBlob` ve `wszFilePath` null) karmalar bağlı modüller için ancak derleme yeniden imzalı değil.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="8fa0c-129">Varsa `SN_TEST_SIGN` belirtilirse, derlemenin tanımlayıcı ad ile imzalı olduğunu belirtmek için ortak dil çalışma zamanı üst değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fa0c-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8fa0c-130">Requirements</span></span>  
 <span data-ttu-id="8fa0c-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fa0c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fa0c-132">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8fa0c-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8fa0c-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8fa0c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8fa0c-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fa0c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fa0c-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8fa0c-135">See Also</span></span>  
 [<span data-ttu-id="8fa0c-136">StrongNameSignatureGeneration Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fa0c-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [<span data-ttu-id="8fa0c-137">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8fa0c-137">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
