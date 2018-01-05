---
title: "ICLRStrongName::StrongNameSignatureVerificationEx Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureVerificationEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 047bc2212e1552a52f0eabf86cc0e86a6945ba39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="9d3b9-102">ICLRStrongName::StrongNameSignatureVerificationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d3b9-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>
<span data-ttu-id="9d3b9-103">Derleme bildirimi sağlanan yolunda bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="9d3b9-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d3b9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d3b9-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d3b9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d3b9-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="9d3b9-106">[in] Taşınabilir yürütülebilir (.exe veya .dll) dosyasını doğrulanacak derleme yolu.</span><span class="sxs-lookup"><span data-stu-id="9d3b9-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="9d3b9-107">[in] `true` , olsa bile gerekli kayıt defteri ayarlarını geçersiz kılmak, aksi takdirde doğrulama gerçekleştirmek için `false`.</span><span class="sxs-lookup"><span data-stu-id="9d3b9-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="9d3b9-108">[out] `true` sağlam ad imzası, doğrulanmış Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="9d3b9-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="9d3b9-109">`pfWasVerified`Ayrıca ayarlamak `false` kayıt defteri ayarları nedeniyle doğrulama başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="9d3b9-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d3b9-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9d3b9-110">Return Value</span></span>  
 <span data-ttu-id="9d3b9-111">`S_OK`doğrulama başarılı olursa; Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="9d3b9-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d3b9-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d3b9-112">Remarks</span></span>  
 <span data-ttu-id="9d3b9-113">[Iclrstrongname::strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) yöntemi benzer bir yetenek sağlar [Iclrstrongname::strongnamesignatureverification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9d3b9-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="9d3b9-114">Ancak, ikinci parametre hem de çıkış parametresi için bir girdi [Iclrstrongname::strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) türü `BOOLEAN` yerine `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="9d3b9-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d3b9-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d3b9-115">Requirements</span></span>  
 <span data-ttu-id="9d3b9-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d3b9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d3b9-117">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9d3b9-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9d3b9-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9d3b9-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d3b9-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d3b9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d3b9-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d3b9-120">See Also</span></span>  
 [<span data-ttu-id="9d3b9-121">StrongNameSignatureVerification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d3b9-121">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="9d3b9-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d3b9-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
