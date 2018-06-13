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
ms.openlocfilehash: f5b4ef7777c9d45c2d255cc2915f8c4ccdeef4a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432616"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="f4da1-102">ICLRStrongName::StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4da1-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>
<span data-ttu-id="f4da1-103">Belirtilen bellek adresinde derleme görüntü ikili bir gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="f4da1-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4da1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4da1-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4da1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f4da1-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="f4da1-106">[in] Eşlenen derleme bildirimi bellek adresi.</span><span class="sxs-lookup"><span data-stu-id="f4da1-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="f4da1-107">[in] Yansımayı bayt cinsinden boyutu `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="f4da1-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="f4da1-108">[in] Görüntü ikili gösterimini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="f4da1-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="f4da1-109">[içinde out] Bayt cinsinden en büyük boyutu, istenen `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="f4da1-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="f4da1-110">Return, bayt cinsinden gerçek boyutu bağlı, `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="f4da1-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4da1-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f4da1-111">Return Value</span></span>  
 <span data-ttu-id="f4da1-112">`S_OK` Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="f4da1-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4da1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4da1-113">Requirements</span></span>  
 <span data-ttu-id="f4da1-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4da1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4da1-115">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f4da1-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f4da1-116">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f4da1-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4da1-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4da1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4da1-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4da1-118">See Also</span></span>  
 [<span data-ttu-id="f4da1-119">StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4da1-119">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="f4da1-120">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4da1-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
