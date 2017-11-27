---
title: "StrongNameSignatureVerificationEx İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureVerificationEx
helpviewer_keywords: StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0aebb53c6718a6812cbe6a6888f389c7b1a52dda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="08629-102">StrongNameSignatureVerificationEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="08629-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="08629-103">Sağlanan yol, derleme bildirimi sağlam ad imzası içeren olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="08629-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="08629-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="08629-104">This function has been deprecated.</span></span> <span data-ttu-id="08629-105">Kullanım [Iclrstrongname::strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="08629-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08629-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08629-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08629-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08629-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="08629-108">[in] Taşınabilir yürütülebilir (.exe veya .dll) dosyasını doğrulanacak derleme yolu.</span><span class="sxs-lookup"><span data-stu-id="08629-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="08629-109">[in] `true` , olsa bile gerekli kayıt defteri ayarlarını geçersiz kılmak, aksi takdirde doğrulama gerçekleştirmek için `false`.</span><span class="sxs-lookup"><span data-stu-id="08629-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="08629-110">[out] `true` sağlam ad imzası, doğrulanmış Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="08629-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="08629-111">`pfWasVerified`Ayrıca ayarlamak `false` kayıt defteri ayarları nedeniyle doğrulama başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="08629-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08629-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="08629-112">Return Value</span></span>  
 <span data-ttu-id="08629-113">`true`doğrulama başarılı olursa; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="08629-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08629-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08629-114">Remarks</span></span>  
 <span data-ttu-id="08629-115">`StrongNameSignatureVerificationEx`benzer bir yetenek sağlar [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="08629-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="08629-116">Ancak, ikinci parametre hem de çıkış parametresi için bir girdi `StrongNameSignatureVerificationEx` türü `BOOLEAN` yerine `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="08629-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08629-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08629-117">Requirements</span></span>  
 <span data-ttu-id="08629-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08629-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08629-119">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="08629-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="08629-120">**Kitaplığı:** bir kaynak olarak mscoree.dll dahil</span><span class="sxs-lookup"><span data-stu-id="08629-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="08629-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08629-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08629-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08629-122">See Also</span></span>  
 [<span data-ttu-id="08629-123">StrongNameSignatureVerificationEx yöntemi</span><span class="sxs-lookup"><span data-stu-id="08629-123">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="08629-124">StrongNameSignatureVerification yöntemi</span><span class="sxs-lookup"><span data-stu-id="08629-124">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="08629-125">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="08629-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
