---
title: "ICLRStrongName::StrongNameGetBlob Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1882936723667b616ff930af00ee899f446521e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="15f26-102">ICLRStrongName::StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15f26-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="15f26-103">Belirtilen arabellek yürütülebilir dosyanın belirtilen adresteki ikili gösterimidir doldurur.</span><span class="sxs-lookup"><span data-stu-id="15f26-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15f26-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15f26-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15f26-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15f26-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="15f26-106">[in] Yüklenecek yürütülebilir dosyanın geçerli bir yol.</span><span class="sxs-lookup"><span data-stu-id="15f26-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="15f26-107">[in] Arabelleğe hangi yürütülebilir dosyası yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="15f26-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="15f26-108">[içinde out] Bayt cinsinden en büyük boyutu, istenen `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="15f26-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="15f26-109">Return, bayt cinsinden gerçek boyutu bağlı, `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="15f26-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15f26-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="15f26-110">Return Value</span></span>  
 <span data-ttu-id="15f26-111">`S_OK`Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="15f26-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15f26-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15f26-112">Requirements</span></span>  
 <span data-ttu-id="15f26-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15f26-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15f26-114">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="15f26-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="15f26-115">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="15f26-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15f26-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15f26-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15f26-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="15f26-117">See Also</span></span>  
 [<span data-ttu-id="15f26-118">StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15f26-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="15f26-119">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15f26-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
