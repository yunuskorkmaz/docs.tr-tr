---
title: "ICLRStrongName::StrongNameKeyDelete Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyDelete
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8fbb6af492007eb0dc2a9ea83c53e3559225428d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="5c3eb-102">ICLRStrongName::StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c3eb-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="5c3eb-103">Belirtilen anahtar kapsayıcısı siler.</span><span class="sxs-lookup"><span data-stu-id="5c3eb-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c3eb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c3eb-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c3eb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c3eb-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="5c3eb-106">[in] Silmek için anahtar kapsayıcı adı.</span><span class="sxs-lookup"><span data-stu-id="5c3eb-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c3eb-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5c3eb-107">Return Value</span></span>  
 <span data-ttu-id="5c3eb-108">`S_OK`Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="5c3eb-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c3eb-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c3eb-109">Remarks</span></span>  
 <span data-ttu-id="5c3eb-110">Kullanım [Iclrstrongname::strongnamekeyınstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) bir kapsayıcıya bir genel/özel anahtar çifti alınacak yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5c3eb-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c3eb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c3eb-111">Requirements</span></span>  
 <span data-ttu-id="5c3eb-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c3eb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c3eb-113">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5c3eb-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5c3eb-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5c3eb-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c3eb-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c3eb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c3eb-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c3eb-116">See Also</span></span>  
 [<span data-ttu-id="5c3eb-117">Strongnamekeyınstall yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c3eb-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="5c3eb-118">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c3eb-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
