---
title: ICLRStrongName::StrongNameHashSize Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameHashSize
helpviewer_keywords:
- ICLRStrongName::StrongNameHashSize method [.NET Framework hosting]
- StrongNameHashSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 4a05ee56-08e4-4f3a-86a9-9b52083d5c0f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91b84a980e8a670b8e8b2970cfc96ddd6f4c33b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218491"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="68b92-102">ICLRStrongName::StrongNameHashSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68b92-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="68b92-103">Belirtilen karma algoritması kullanarak bir karma için gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="68b92-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68b92-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68b92-104">Syntax</span></span>  
  
```  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68b92-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68b92-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="68b92-106">[in] Arabellek boyutunu hesaplamak için kullanılan karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="68b92-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="68b92-107">[out] Döndürülen arabellek bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="68b92-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68b92-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="68b92-108">Return Value</span></span>  
 <span data-ttu-id="68b92-109">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="68b92-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68b92-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68b92-110">Requirements</span></span>  
 <span data-ttu-id="68b92-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68b92-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68b92-112">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="68b92-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="68b92-113">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="68b92-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68b92-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68b92-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68b92-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68b92-115">See also</span></span>

- [<span data-ttu-id="68b92-116">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68b92-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
