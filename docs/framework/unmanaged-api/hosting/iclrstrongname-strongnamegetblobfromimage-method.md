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
ms.openlocfilehash: ad3b151165eb233bd3a4a78d8f4d612a696b7e93
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135104"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="68f22-102">ICLRStrongName::StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68f22-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>
<span data-ttu-id="68f22-103">Belirtilen bellek adresindeki derleme görüntüsünün ikili gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="68f22-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68f22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68f22-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68f22-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68f22-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="68f22-106">'ndaki Eşlenen derleme bildiriminin bellek adresi.</span><span class="sxs-lookup"><span data-stu-id="68f22-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="68f22-107">'ndaki `pbBase`konumundaki görüntünün bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="68f22-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="68f22-108">'ndaki Görüntünün ikili gösterimini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="68f22-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="68f22-109">[in, out] `pbBlob`istenen en büyük boyut (bayt cinsinden).</span><span class="sxs-lookup"><span data-stu-id="68f22-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="68f22-110">Dönüş sonrasında, `pbBlob`bayt cinsinden gerçek boyut.</span><span class="sxs-lookup"><span data-stu-id="68f22-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68f22-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="68f22-111">Return Value</span></span>  
 <span data-ttu-id="68f22-112">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](https://go.microsoft.com/fwlink/?LinkId=213878) ).</span><span class="sxs-lookup"><span data-stu-id="68f22-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68f22-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68f22-113">Requirements</span></span>  
 <span data-ttu-id="68f22-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68f22-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68f22-115">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="68f22-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="68f22-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="68f22-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68f22-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68f22-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f22-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68f22-118">See also</span></span>

- [<span data-ttu-id="68f22-119">StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68f22-119">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="68f22-120">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68f22-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
