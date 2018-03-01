---
title: "ICLRStrongName::StrongNameKeyDelete Yöntemi"
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
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1b3a1d742ac2ad74d327afe4dce097d0f11e5cfe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="d4981-102">ICLRStrongName::StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4981-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="d4981-103">Belirtilen anahtar kapsayıcısı siler.</span><span class="sxs-lookup"><span data-stu-id="d4981-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4981-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4981-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4981-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4981-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="d4981-106">[in] Silmek için anahtar kapsayıcı adı.</span><span class="sxs-lookup"><span data-stu-id="d4981-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4981-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d4981-107">Return Value</span></span>  
 <span data-ttu-id="d4981-108">`S_OK`Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="d4981-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4981-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4981-109">Remarks</span></span>  
 <span data-ttu-id="d4981-110">Kullanım [Iclrstrongname::strongnamekeyınstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) bir kapsayıcıya bir genel/özel anahtar çifti alınacak yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d4981-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4981-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4981-111">Requirements</span></span>  
 <span data-ttu-id="d4981-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4981-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4981-113">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d4981-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d4981-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d4981-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4981-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4981-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4981-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4981-116">See Also</span></span>  
 [<span data-ttu-id="d4981-117">StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4981-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="d4981-118">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4981-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
