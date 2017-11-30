---
title: "ICLRStrongName::StrongNameKeyInstall Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyInstall
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 241421761b87bf9f3baf7315c2ac8e9ebd499486
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="fd0dc-102">ICLRStrongName::StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd0dc-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="fd0dc-103">Bir ortak/özel anahtar çifti bir kapsayıcıya alır.</span><span class="sxs-lookup"><span data-stu-id="fd0dc-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd0dc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd0dc-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd0dc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd0dc-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="fd0dc-106">[in] Anahtar kapsayıcı adı.</span><span class="sxs-lookup"><span data-stu-id="fd0dc-106">[in] The name of the key container.</span></span> <span data-ttu-id="fd0dc-107">`wszKeyContainer`boş olmayan bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fd0dc-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="fd0dc-108">[in] İkili anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="fd0dc-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="fd0dc-109">[in] Bayt olarak boyutu, `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="fd0dc-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd0dc-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fd0dc-110">Return Value</span></span>  
 <span data-ttu-id="fd0dc-111">`S_OK`Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="fd0dc-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd0dc-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd0dc-112">Remarks</span></span>  
 <span data-ttu-id="fd0dc-113">Kullanım [Iclrstrongname::strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) anahtar kapsayıcısını silmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="fd0dc-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd0dc-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd0dc-114">Requirements</span></span>  
 <span data-ttu-id="fd0dc-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd0dc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd0dc-116">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="fd0dc-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fd0dc-117">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fd0dc-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd0dc-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd0dc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd0dc-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd0dc-119">See Also</span></span>  
 [<span data-ttu-id="fd0dc-120">StrongNameKeyDelete yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd0dc-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="fd0dc-121">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd0dc-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
