---
title: ICLRStrongName::StrongNameFreeBuffer Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfc4cb503c7d94345ede34de1788667857946e0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433144"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="7d5cd-102">ICLRStrongName::StrongNameFreeBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d5cd-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="7d5cd-103">Güçlü ad yöntemi önceki çağrısıyla ayrıldı bellek boşaltır [Iclrstrongname::strongnamegetpublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [Iclrstrongname::strongnametokenfrompublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), veya [ Iclrstrongname::strongnamesignaturegeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span><span class="sxs-lookup"><span data-stu-id="7d5cd-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d5cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d5cd-104">Syntax</span></span>  
  
```  
HRESULT StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d5cd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d5cd-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="7d5cd-106">[in] Bellek boşaltmak için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7d5cd-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d5cd-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7d5cd-107">Return Value</span></span>  
 <span data-ttu-id="7d5cd-108">`S_OK` Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="7d5cd-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d5cd-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d5cd-109">Requirements</span></span>  
 <span data-ttu-id="7d5cd-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d5cd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d5cd-111">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7d5cd-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7d5cd-112">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7d5cd-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d5cd-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d5cd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d5cd-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d5cd-114">See Also</span></span>  
 [<span data-ttu-id="7d5cd-115">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d5cd-115">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
