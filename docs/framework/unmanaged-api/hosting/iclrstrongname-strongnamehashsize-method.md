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
ms.openlocfilehash: 0c09832d296033b0790d3e6282763a1163abdfd2
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361105"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="dbba2-102">ICLRStrongName::StrongNameHashSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dbba2-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="dbba2-103">Belirtilen karma algoritması kullanarak bir karma için gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="dbba2-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbba2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbba2-104">Syntax</span></span>  
  
```  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbba2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dbba2-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="dbba2-106">[in] Arabellek boyutunu hesaplamak için kullanılan karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="dbba2-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="dbba2-107">[out] Döndürülen arabellek bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="dbba2-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbba2-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dbba2-108">Return Value</span></span>  
 <span data-ttu-id="dbba2-109">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="dbba2-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbba2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dbba2-110">Requirements</span></span>  
 <span data-ttu-id="dbba2-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbba2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbba2-112">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="dbba2-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="dbba2-113">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="dbba2-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbba2-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbba2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbba2-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dbba2-115">See Also</span></span>  
 [<span data-ttu-id="dbba2-116">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dbba2-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
