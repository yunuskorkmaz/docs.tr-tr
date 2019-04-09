---
title: ICLRStrongName::StrongNameGetBlobFromImage Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetBlobFromImage method [.NET Framework hosting]
ms.assetid: 0f5a2ec8-e776-4fd8-bda6-937b6834575a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fa83f55a03ebfff9ae88217b01c86272bf0de93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178977"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="416cc-102">ICLRStrongName::StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="416cc-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>
<span data-ttu-id="416cc-103">Belirtilen bellek adresinde derleme yansıma ikili gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="416cc-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="416cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="416cc-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="416cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="416cc-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="416cc-106">[in] Eşlenen derleme bildirimi bellek adresi.</span><span class="sxs-lookup"><span data-stu-id="416cc-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="416cc-107">[in] Bayt cinsinden görüntü boyutu `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="416cc-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="416cc-108">[in] Görüntü ikili gösterimini içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="416cc-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="416cc-109">[out içinde] Bayt cinsinden en büyük boyutu, istenen `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="416cc-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="416cc-110">İade, bayt cinsinden gerçek boyutu bağlı, `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="416cc-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="416cc-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="416cc-111">Return Value</span></span>  
 `S_OK` <span data-ttu-id="416cc-112">yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="416cc-112">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="416cc-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="416cc-113">Requirements</span></span>  
 <span data-ttu-id="416cc-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="416cc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="416cc-115">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="416cc-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="416cc-116">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="416cc-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="416cc-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="416cc-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="416cc-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="416cc-118">See also</span></span>

- [<span data-ttu-id="416cc-119">StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="416cc-119">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="416cc-120">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="416cc-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
