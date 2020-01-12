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
ms.openlocfilehash: a0bcc62a1715fb455f0affee64a351cabe0ba3f6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901132"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="41d03-102">ICLRStrongName::StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41d03-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>
<span data-ttu-id="41d03-103">Belirtilen bellek adresindeki derleme görüntüsünün ikili gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="41d03-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41d03-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41d03-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41d03-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41d03-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="41d03-106">'ndaki Eşlenen derleme bildiriminin bellek adresi.</span><span class="sxs-lookup"><span data-stu-id="41d03-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="41d03-107">'ndaki `pbBase`konumundaki görüntünün bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="41d03-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="41d03-108">'ndaki Görüntünün ikili gösterimini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="41d03-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="41d03-109">[in, out] `pbBlob`istenen en büyük boyut (bayt cinsinden).</span><span class="sxs-lookup"><span data-stu-id="41d03-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="41d03-110">Dönüş sonrasında, `pbBlob`bayt cinsinden gerçek boyut.</span><span class="sxs-lookup"><span data-stu-id="41d03-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41d03-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="41d03-111">Return Value</span></span>  
 <span data-ttu-id="41d03-112">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="41d03-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41d03-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41d03-113">Requirements</span></span>  
 <span data-ttu-id="41d03-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41d03-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41d03-115">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="41d03-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="41d03-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="41d03-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41d03-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41d03-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41d03-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41d03-118">See also</span></span>

- [<span data-ttu-id="41d03-119">StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41d03-119">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="41d03-120">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41d03-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
