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
ms.openlocfilehash: 82e18db2f5b911f0e7895959119edd7d2c722f3b
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763142"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="008fe-102">ICLRStrongName::StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="008fe-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>
<span data-ttu-id="008fe-103">Belirtilen bellek adresindeki derleme görüntüsünün ikili gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="008fe-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="008fe-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="008fe-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="008fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="008fe-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="008fe-106">'ndaki Eşlenen derleme bildiriminin bellek adresi.</span><span class="sxs-lookup"><span data-stu-id="008fe-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="008fe-107">'ndaki İçindeki görüntünün bayt cinsinden boyutu `pbBase` .</span><span class="sxs-lookup"><span data-stu-id="008fe-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="008fe-108">'ndaki Görüntünün ikili gösterimini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="008fe-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="008fe-109">[in, out] İstenen en büyük boyut (bayt) `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="008fe-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="008fe-110">Dönüş sonrasında, bayt cinsinden gerçek boyut `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="008fe-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="008fe-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="008fe-111">Return Value</span></span>  
 <span data-ttu-id="008fe-112">`S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="008fe-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="008fe-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="008fe-113">Requirements</span></span>  
 <span data-ttu-id="008fe-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="008fe-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="008fe-115">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="008fe-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="008fe-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="008fe-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="008fe-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="008fe-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="008fe-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="008fe-118">See also</span></span>

- [<span data-ttu-id="008fe-119">StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="008fe-119">StrongNameGetBlob Method</span></span>](iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="008fe-120">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="008fe-120">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
