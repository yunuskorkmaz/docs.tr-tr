---
title: ICLRStrongName::StrongNameGetBlob Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ba606230be7a81fc42644c2fd3883a989bf37ac
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498997"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="c3c34-102">ICLRStrongName::StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3c34-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="c3c34-103">Belirtilen arabellek, yürütülebilir dosyanın belirtilen adreste ikili gösterimini ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="c3c34-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3c34-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3c34-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3c34-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3c34-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="c3c34-106">[in] Yüklenen yürütülebilir dosyanın geçerli bir yol.</span><span class="sxs-lookup"><span data-stu-id="c3c34-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="c3c34-107">[in] Arabelleğe yürütülebilir dosyayı yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="c3c34-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="c3c34-108">[out içinde] Bayt cinsinden en büyük boyutu, istenen `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="c3c34-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="c3c34-109">İade, bayt cinsinden gerçek boyutu bağlı, `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="c3c34-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3c34-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c3c34-110">Return Value</span></span>  
 <span data-ttu-id="c3c34-111">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="c3c34-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3c34-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3c34-112">Requirements</span></span>  
 <span data-ttu-id="c3c34-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3c34-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3c34-114">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c3c34-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c3c34-115">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c3c34-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3c34-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3c34-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3c34-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3c34-117">See also</span></span>
- [<span data-ttu-id="c3c34-118">StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3c34-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="c3c34-119">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3c34-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
