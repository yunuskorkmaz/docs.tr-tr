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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5d60b9a9ae566b5bd686b27b2e09861a8414979
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190021"
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="dca95-102">StrongNameSignatureGenerationEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="dca95-102">StrongNameSignatureGenerationEx Function</span></span>
<span data-ttu-id="dca95-103">Belirtilen bayraklar göre belirtilen derleme için tanımlayıcı ad imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dca95-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="dca95-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="dca95-104">This function has been deprecated.</span></span> <span data-ttu-id="dca95-105">Kullanım [Iclrstrongname::strongnamesignaturegenerationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="dca95-105">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dca95-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dca95-106">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="dca95-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dca95-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="dca95-108">[in] Tanımlayıcı ad imzası oluşturulacak derleme bildirimi içeren dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="dca95-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="dca95-109">[in] Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="dca95-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="dca95-110">Varsa `pbKeyBlob` boş `wszKeyContainer` şifreleme hizmeti sağlayıcısı (CSP) geçerli bir kapsayıcıda belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dca95-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="dca95-111">Bu durumda, bir kapsayıcıda depolanan bir anahtar çifti dosyasını imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dca95-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="dca95-112">Varsa `pbKeyBlob` anahtar çiftini varsayılır anahtar ikili büyük nesne içinde (BLOB) dahil edilmek üzere null değil.</span><span class="sxs-lookup"><span data-stu-id="dca95-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="dca95-113">[in] Ortak/özel anahtar çifti için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dca95-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="dca95-114">Win32 oluşturulan biçimde bu çiftidir `CryptExportKey` işlevi.</span><span class="sxs-lookup"><span data-stu-id="dca95-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="dca95-115">Varsa `pbKeyBlob` null, belirtilen anahtar kapsayıcısı olan `wszKeyContainer` anahtar çiftini içerdiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="dca95-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="dca95-116">[in] Bayt cinsinden boyutu, `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="dca95-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="dca95-117">[out] Ortak dil çalışma zamanı imza döndüren konumu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dca95-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="dca95-118">Varsa `ppbSignatureBlob` olduğundan çalışma zamanı tarafından belirtilen dosyada imza null depolar `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="dca95-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="dca95-119">Varsa `ppbSignatureBlob` olan null, ortak dil çalışma zamanı imza döndürmek alan ayırır.</span><span class="sxs-lookup"><span data-stu-id="dca95-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="dca95-120">Çağıranın kullanarak bu alan boşaltmanız gerekir [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="dca95-120">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="dca95-121">[out] Baytlarında döndürülen imza boyutu.</span><span class="sxs-lookup"><span data-stu-id="dca95-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="dca95-122">[in] Bir veya daha fazla aşağıdaki değerlerden biri:</span><span class="sxs-lookup"><span data-stu-id="dca95-122">[in] One or more of the following values:</span></span>  
  
-   <span data-ttu-id="dca95-123">`SN_SIGN_ALL_FILES` (0x00000001) - bağlı olan modüller için tüm karmaları yeniden oynatmanız.</span><span class="sxs-lookup"><span data-stu-id="dca95-123">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
-   <span data-ttu-id="dca95-124">`SN_TEST_SIGN` (0x00000002) - derlemeyi test imzalayın.</span><span class="sxs-lookup"><span data-stu-id="dca95-124">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dca95-125">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dca95-125">Return Value</span></span>  
 <span data-ttu-id="dca95-126">`true` başarıyla tamamlandığında; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="dca95-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dca95-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dca95-127">Remarks</span></span>  
 <span data-ttu-id="dca95-128">İçin null belirtin `wszFilePath` imza oluşturmadan imza boyutunu hesaplamak için.</span><span class="sxs-lookup"><span data-stu-id="dca95-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="dca95-129">İmza ya da doğrudan dosyasında depolanan veya arayana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="dca95-129">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="dca95-130">Varsa `SN_SIGN_ALL_FILES` belirtildi ancak ortak anahtar dahil değildir (her ikisi de `pbKeyBlob` ve `wszFilePath` null) karmalar bağlı modüller için ancak derleme yeniden imzalı değil.</span><span class="sxs-lookup"><span data-stu-id="dca95-130">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="dca95-131">Varsa `SN_TEST_SIGN` belirtilirse, derlemenin tanımlayıcı ad ile imzalı olduğunu belirtmek için ortak dil çalışma zamanı üst değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="dca95-131">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="dca95-132">Varsa `StrongNameSignatureGenerationEx` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.</span><span class="sxs-lookup"><span data-stu-id="dca95-132">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dca95-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dca95-133">Requirements</span></span>  
 <span data-ttu-id="dca95-134">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dca95-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dca95-135">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="dca95-135">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="dca95-136">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="dca95-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dca95-137">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dca95-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca95-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dca95-138">See also</span></span>

- [<span data-ttu-id="dca95-139">StrongNameSignatureGenerationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dca95-139">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="dca95-140">StrongNameSignatureGeneration Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dca95-140">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="dca95-141">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dca95-141">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
