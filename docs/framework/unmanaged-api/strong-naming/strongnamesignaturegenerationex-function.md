---
title: "StrongNameSignatureGenerationEx İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f68befd145649e6d8921e160d302cdb81000a9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="053fa-102">StrongNameSignatureGenerationEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="053fa-102">StrongNameSignatureGenerationEx Function</span></span>
<span data-ttu-id="053fa-103">Belirtilen bayrakları göre belirtilen derleme için bir tanımlayıcı ad imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="053fa-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="053fa-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="053fa-104">This function has been deprecated.</span></span> <span data-ttu-id="053fa-105">Kullanım [Iclrstrongname::strongnamesignaturegenerationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="053fa-105">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="053fa-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="053fa-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="053fa-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="053fa-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="053fa-108">[in] Tanımlayıcı ad imzası oluşturulmayacak derleme bildirimi içeren dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="053fa-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="053fa-109">[in] Ortak/özel anahtar çiftini içeren anahtar kapsayıcı adı.</span><span class="sxs-lookup"><span data-stu-id="053fa-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="053fa-110">Varsa `pbKeyBlob` null, `wszKeyContainer` şifreleme hizmeti sağlayıcısı (CSP) geçerli bir kapsayıcıda belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="053fa-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="053fa-111">Bu durumda, kapsayıcısında depolanan anahtar çifti dosyasını imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="053fa-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="053fa-112">Varsa `pbKeyBlob` anahtar çifti varsayılır anahtar ikili büyük nesne (BLOB) dahil edilmek üzere null değil.</span><span class="sxs-lookup"><span data-stu-id="053fa-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="053fa-113">[in] Ortak/özel anahtar çifti için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="053fa-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="053fa-114">Bu çiftidir Win32 tarafından oluşturulan biçiminde `CryptExportKey` işlevi.</span><span class="sxs-lookup"><span data-stu-id="053fa-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="053fa-115">Varsa `pbKeyBlob` null, belirtilen anahtar kapsayıcısı olan `wszKeyContainer` anahtar çiftini içeren varsayılır.</span><span class="sxs-lookup"><span data-stu-id="053fa-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="053fa-116">[in] Bayt olarak boyutu, `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="053fa-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="053fa-117">[out] Ortak dil çalışma zamanı imza döndüğü konuma bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="053fa-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="053fa-118">Varsa `ppbSignatureBlob` olduğu çalışma zamanı tarafından belirtilen dosyada imza null depolar `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="053fa-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="053fa-119">Varsa `ppbSignatureBlob` olan null, ortak dil çalışma zamanı imza döndürmek üzere alan ayırır.</span><span class="sxs-lookup"><span data-stu-id="053fa-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="053fa-120">Arayan kullanarak bu alanı boş gerekir [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="053fa-120">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="053fa-121">[out] Döndürülen imza bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="053fa-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="053fa-122">[in] Bir veya daha fazla aşağıdaki değerlerden biri:</span><span class="sxs-lookup"><span data-stu-id="053fa-122">[in] One or more of the following values:</span></span>  
  
-   <span data-ttu-id="053fa-123">`SN_SIGN_ALL_FILES`(0x00000001) - bağlantılı modülleri için tüm karmaları yeniden hesaplamak.</span><span class="sxs-lookup"><span data-stu-id="053fa-123">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
-   <span data-ttu-id="053fa-124">`SN_TEST_SIGN`(0x00000002) - test-oturum derleme.</span><span class="sxs-lookup"><span data-stu-id="053fa-124">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="053fa-125">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="053fa-125">Return Value</span></span>  
 <span data-ttu-id="053fa-126">`true`başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="053fa-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="053fa-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="053fa-127">Remarks</span></span>  
 <span data-ttu-id="053fa-128">İçin null belirtin `wszFilePath` imza oluşturmadan imza boyutu hesaplanamadı.</span><span class="sxs-lookup"><span data-stu-id="053fa-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="053fa-129">İmza ya da doğrudan dosyasında depolanan veya yapana.</span><span class="sxs-lookup"><span data-stu-id="053fa-129">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="053fa-130">Varsa `SN_SIGN_ALL_FILES` belirtildi ancak bir ortak anahtar dahil değildir (her ikisi de `pbKeyBlob` ve `wszFilePath` null) bağlantılı modülleri için karmaları yeniden ancak derleme yeniden imzalı değil.</span><span class="sxs-lookup"><span data-stu-id="053fa-130">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="053fa-131">Varsa `SN_TEST_SIGN` belirtilirse, ortak dil çalışma zamanı üstbilgisi derleme tanımlayıcı bir ad ile imzalı olduğunu belirtmek için değişiklik yok.</span><span class="sxs-lookup"><span data-stu-id="053fa-131">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="053fa-132">Varsa `StrongNameSignatureGenerationEx` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="053fa-132">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="053fa-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="053fa-133">Requirements</span></span>  
 <span data-ttu-id="053fa-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="053fa-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="053fa-135">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="053fa-135">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="053fa-136">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="053fa-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="053fa-137">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="053fa-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="053fa-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="053fa-138">See Also</span></span>  
 [<span data-ttu-id="053fa-139">StrongNameSignatureGenerationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="053fa-139">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [<span data-ttu-id="053fa-140">StrongNameSignatureGeneration Yöntemi</span><span class="sxs-lookup"><span data-stu-id="053fa-140">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [<span data-ttu-id="053fa-141">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="053fa-141">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
